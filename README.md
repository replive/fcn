# fcn
free connect your private network from anywhere

# 1. fcn是什么

fcn[`free connect`]是一款傻瓜式的一键接入私有网络的工具, 由客户服务端和客户端组成

fcn使用fcn公网数据服务器以及数据加密技术，将用户客户端虚拟接入客户服务端私有网络

fcn = `fcn_server` + `fcn_client`

## fcn_server

目前支持linux x86 + x64平台，arm平台待支持中, 下一步考虑添加windows服务器接入支持

|文件位置|描述
|-------|---
|server_linux\ `client` | 接入服务器x86平台bin
|server_linux\ `client64` | 接入服务器x64平台bin
|server_linux\ `server.conf` | 服务器配置文件

## fcn_client

目前只支持windows x86/x64 

|文件位置|描述
|-------|---
|client_windows\ `x86` | 接入客户端x86平台bin
|client_windows\ `x64` | 接入客户端x64平台bin

# 2. fcn使用

## 2.1 运行客户服务端

首先配置server.conf配置文件, 注意目前测试帐户 `FCN_0000-FCN_9999`, 每个帐户限速100KB/s

请用户随机挑选测试帐户，并且设置自己的唯一服务器名，以防止帐户冲突

|文件位置|描述
|-------|---
| [uid] | FCN_[0001-9999] 8字符用户ID *必填
| [name] | 服务器名,程序通过该名称标示服务器, 同一个uid不可重复
| [psk]| 连接密码, 建议不填, 由服务端启动时随机生成
| [nat_nic] | 虚拟接入后连接的服务器网卡名, 建议不填
| [dhcp_ip/dhcp_mask] |  虚拟接入后DHCP网段, 建议不填

ROOT权限运行
```shell
./client            # 命令行形式直接运行,临时测试
nohup ./client &    # 在后台运行
```

## 2.2 运行windows客户端

主界面添加服务器,填写对应的连接参数,连接,成功后,windows客户端即接入了服务器对应局域网

注:第一次连接时会自动安装虚拟网卡驱动,需用户确认同意

# 3. fcn安全吗？

## 3.1 fcn通信安全机制

fcn使用了数字证书、tls以及aes 256bit加密技术，用户网络数据全程加密，5分钟左右自动更新会话密钥，确保用户数据不会被截获解密或者中间人欺骗。

fcn公网服务器不会收集用户的任何网络数据，后期考虑开放用户加密接口，以便用户实现自定义的端到端私有加密。

## 3.2 fcn本地安全

fcn二进制文件发布前经过针对性的混淆加密处理，尽可能防止用户的加密配置文件被黑客攻击解密。

## 3.3 fcn是专业软件

fcn软件作者是boywhp，从事网络安全行业多年，是看雪安全论坛（bbs.pediy.com）高级会员，在业界发表过多篇网络安全技术文章。

当然作者也深知在网络攻防上，没有绝对的安全，因此在这里还请各位同行手下留情。

