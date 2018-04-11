安装libsodium，让后端支持更多的加密方式（以下命令一个个输入）：

yum -y groupinstall "Development Tools"
wget https://github.com/jedisct1/libsodium/releases/download/1.0.10/libsodium-1.0.10.tar.gz
tar xf libsodium-1.0.10.tar.gz && cd libsodium-1.0.10
./configure && make -j2 && make install
echo /usr/local/lib > /etc/ld.so.conf.d/usr_local_lib.conf
ldconfig
再次回到root目录下：

cd /root
下载后端程序：

git clone -b manyuser https://github.com/shadowsocksrr/shadowsocksr.git
进入到shadowsocksr目录：

cd shadowsocksr
安装依赖：

./setup_cymysql.sh
初始化配置文件：

./initcfg.sh
修改userapiconfig.py的接口为glzjinmod

vi userapiconfig.py
如图：



修改user-config.json，将connect_verbose_info的值改为1，另外根据自己的需要修改相关的加密方式、混淆、协议等等。

vi user-config.json
如图：



修改usermysql.json，将数据库信息改为你自己的，另外记得修改node_id的值为1：

vi usermysql.json
如图：



测试运行一下后端，看看是否正常：

python server.py
看到如图回显则说明后端正常：



按键盘组合键Ctrl+C退出，然后将后端放到后台运行：

./run.sh
