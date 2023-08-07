# Mac本安装iTerm2配置rz sz 环境
rz 可以很方便的从客户端传文件到服务器，sz也可以很方便的从服务器传文件到客户端，就算中间隔着跳板机也不影响。
在mac下试了一下，mac的终端是不支持的，需要下载item2。另外不能在mac下用expect 自动登录服务器执行rz或sz ，否则终端会挂掉。
## 安装iTerm2
建议去官网下载 http://www.iterm2.com/
## mac环境下iterm2安装sz、rz  
参考了很多文章步骤很简单，直接一个命令brew install lrzsz，可是自己操作时并没有brew这个命令，总是not found command。所以在此之前要先安装brew。
一般在unix或者类unix的linux系统上使用yunm或者apt-get，但在Mac osx上不好使，brew是homebrew的简称，它的功能类似yum或者apt-get，是max osx上的软件包管理工具。
具体可以网上自行搜索安装brew

安装使用如下命令：
```
brew install lrzsz
```
等待安装完成。
## 本地环境配置rz sz上传和下载脚本
```
#进入 /usr/local/bin目录
cd /usr/local/bin
 
#下载两个脚本
sudo wget https://gist.githubusercontent.com/sy-records/1b3010b566af42f57fa6fa38138dd22a/raw/2bfe590665d3b0e6c8223623922474361058920c/iterm2-send-zmodem.sh
sudo wget https://gist.githubusercontent.com/sy-records/40f4ba22e3fbdeedf58463b067798962/raw/b32d2f7ac3fa54acca81be3664797cebb724690f/iterm2-recv-zmodem.sh
 
#加权限
sudo chmod 777 /usr/local/bin/iterm2-*
``` 
## iterm2配置
左上角iterm2->preferences->Profiles→Advanced->Edit  
左下角点+后双击表格添加2行，如上图所示，完成后点击右下角close

| Triggers | Action | Parameters | Instant | Enable |
| --- | --- | --- | --- | --- |
\\*\\*B0100 |	Run Silent Coprocess | /usr/local/bin/iterm2-send-zmodem.sh | Y  | Y  |
\\*\\*B00000000000000 | Run Silent Coprocess | /usr/local/bin/iterm2-recv-zmodem.sh | Y | Y  |
