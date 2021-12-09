# Linux-NetSpeed

wget: command not found的解决方法:yum -y install wget 回车即可

如果提示 curl: command not found ，那是因为你的 VPS 没装 Curl

ubuntu/debian 系统安装 Curl 方法: apt-get update -y && apt-get install curl -y

centos 系统安装 Curl 方法: yum update -y && yum install curl -y

ubuntu/debian出现和net相关功能不能使用时，需要安装net-tools 命令：apt-get update -y && apt-get install net-tools -y

history -c 命令,清除所有历史记录

nano ~/.bash_history 该文件即为历史记录存储文件，我们随意修改

ubuntu出现You might want to run 'apt --fix-broken install' to correct these时（有时候证书安装出错也是这个原因），需要安装：apt-get --fix-broken install

出现dpkg: error: dpkg frontend is locked by another process，需要执行：rm /var/lib/dpkg/lock,然后输入：dpkg --configure -a,重新启动

### 魔改版bbr加速：
``` bash
wget -N --no-check-certificate "https://raw.githubusercontent.com/wangxiaoke123/Linux-NetSpeed/master/tcp.sh" && chmod +x tcp.sh && ./tcp.sh
``` 
### bbrplus加速：
``` bash
wget -N --no-check-certificate "https://raw.githubusercontent.com/chiakge/Linux-NetSpeed/master/tcp.sh" && chmod +x tcp.sh && ./tcp.sh
``` 
### OpenVZ BBR debian/ubuntu加速
``` 
wget --no-check-certificate https://github.com/tcp-nanqinlang/lkl-rinetd/releases/download/1.1.0/tcp_nanqinlang-rinetd-debianorubuntu.sh
bash tcp_nanqinlang-rinetd-debianorubuntu.sh
```
### OpenVZ BBR centos7加速
```
wget --no-check-certificate https://github.com/tcp-nanqinlang/lkl-rinetd/releases/download/1.1.0/tcp_nanqinlang-rinetd-centos.sh
bash tcp_nanqinlang-rinetd-centos.sh
```
查看状态 ./tcp.sh

需要按8，进行系统优化

执行  lsmod | grep bbr ，以检测 BBR 是否开启

### 1.四网回程路由：
``` bash
wget https://raw.githubusercontent.com/nanqinlang-script/testrace/master/testrace.sh && bash testrace.sh
```
---

### 2.测试回程路由（国外到本地）：
centos7+：
``` bash
yum install -y wget unzip && wget https://cdn.ipip.net/17mon/besttrace4linux.zip && unzip besttrace4linux.zip && chmod +x  besttrace
``` 
Ubuntu/Debian：
``` bash
apt install -y wget zip && wget https://cdn.ipip.net/17mon/besttrace4linux.zip && unzip besttrace* && chmod +x besttrace
``` 
然后执行以下命令：
``` bash
./besttrace 你的本地ip -g cn
``` 
### 硬件信息：
``` bash
wget -qO- --no-check-certificate https://raw.githubusercontent.com/oooldking/script/master/superbench.sh | bash
``` 
### 服务器测速代码 
``` bash
curl -s https://raw.githubusercontent.com/sivel/speedtest-cli/master/speedtest.py | python -
``` 
### 测试国内多地的速度
``` bash
curl -O https://raw.githubusercontent.com/wangn9900/trojan/master/gospeed.sh && chmod +x gospeed.sh && ./gospeed.sh
``` 
查看端口是否被占用lsof -i:53

查看所有端口对应的PID 命令为：netstat -nlp

查看某个端口对应的PID 命令为：netstat -nlp | grep :8083

杀死某进程PID,例如为792 然后 kill -9 792或者kill 792

查看端口是否开启 
netstat -nupl (UDP类型的端口)
netstat -ntpl (TCP类型的端口)

rm -rf  删除文件或文件夹

mkdir aaa 在当前目录下创建 aaa 目录

Linux自带解压命令 tar xvzf file.tar.gz

mv 解压目录 www     (命令是将该目录名称改为www)

生成100MB测试文件代码：dd if=/dev/urandom of=100mb.bin bs=1M count=100

编辑hosts：vi /etc/hosts

换源步骤：

输入命令 nano /etc/apt/sources.list

将里面的东西注释掉，贴入镜像源代码

Ctrl+X 退出保存

## 使用 Docker 一键安装 HTML5 Speedtest

首先安装 Docker
``` bash
curl -sSL https://get.docker.com/ | sh
```
``` bash
systemctl start docker
```
``` bash
systemctl enable docker
```
安装HTML5 Speedtest
``` bash
docker run -d -p 6688:80 ilemonrain/html5-speedtest:alpine
```
