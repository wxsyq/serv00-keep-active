# serv00-keep-active  

通过SSH方式每3天登录一次服务器来保活。  
只使用GitHub的Action来实现，没有任何其他的代码（包括Python，JS等等）  

## 怎么使用  
### 前期准备  
1. 生成你的SSH密钥文件对  
    - 使用命令 `ssh-keygen -t rsa -b 4096` 产生RSA密钥对。密钥文件位于 `/home/your_user/.ssh/`, `id_rsa` 是私钥文件, `id_rsa_pub` 是公钥文件  
    - 使用命令 `cat ~/.ssh/id_rsa` 显示私钥的值并拷贝粘贴到repo的参数 `SSH_PRIVATE_KEY`值里。  
    - 使用命令 `ssh-copy-id username@server_ip` 发送你的公钥文件到 serv00 服务器。  
2. 产生telegram机器人, 获取 token 和 chat_id  
    - 在telegram里找到 `@BotFather` , 根据提示新建一个机器人并获取到 `BOT_TOKEN`  
    - 访问 `https://api.telegram.org/bot<YourBotToken>/getUpdates` 在返回的JSON里查找 `chat_id` (如果返回的JSON是空的, 需要你先在telegram里给机器人发送任意一个消息，然后再重新获取chat_id)  

### 步骤
1. Fork本repo
2. 在你的repo里找到 `Settings` -> `Secrets and variables` -> `Actions`, 点击`New repository secret`添加下列参数:

| secret | value |
|-------|-------|
| SERVER_IP | your serv00 IP |
| USERNAME | your serv00 ssh usename |
| SSH_PRIVATE_KEY | your private key |
| TELEGRAM_BOT_TOKEN | your telegram bot token |
| TELEGRAM_CHAT_ID | your telegram chat id |  
