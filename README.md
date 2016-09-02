# docker

##docker 使用实践
一、查看系统版本以及内核
$cat /etc/issue 

$uname -r 

因为docker要求服务CentOS6以上，kernel 版本必须2.6.32-431或更高

要将Docker安装到CentOS上，首先启用EPEL软件库，然后使用yum命令：

sudo yum install docker-io 
 
sudo service docker start 
 
sudo chkconfig docker on  

将Docker安装到CentOS上后，你需要将自己添加到docker群组，那样才能以非root用户的身份来运行Docker。为此，使用这个命令：

sudo usermod -a -G docker $USER  

退出，重新登录，以激活群组变更。

至此，你应该能够以非特权用户的身份来运行docker命令了。

（二）

列出所有的image

$ docker images 
运行Container

$ docker run --name shell -i -t ubuntu:latest /bin/bash 
 
$ docker run -t -i efd1e7457182 /bin/bash 
两个参数，-t表示给容器tty终端，-i表示可以interactive，可以交互。

退出

$ exit 
编写Dockerfile，运行docker build指令，就可以构建自己的Image

Dockerfile提供了CMD和ENTRYPOINT这2个指令，允许你指定一个Image启动时的默认命令。CMD和ENTRYPOINT的区别是CMD的参数可以由docker run指令指定的参数覆盖，而ENTRYPOINT则不可以。

使用Dockerfile创建image:

$ sudo docker build -t "sloan/centos-latest:v4" . 
其中-t标记添加tag,指定新的镜像的用户信息。 "."Dockerfile所有的路径。

修改image的tag:

$ sudo docker tag e5b5df13b85e sloan/centos-latest 
 
$ sudo docker images sloan/centos-latest 
上传镜像：

$ sudo docker push sloan/centos-latest 
查看系统的版本和内核：

$cat /etc/issue 
 
$uname -r 
因为docker要求服务CentOS6以上，kernel 版本必须2.6.32-431或更高

要将Docker安装到CentOS上，首先启用EPEL软件库，然后使用yum命令：

sudo yum install docker-io 
 
sudo service docker start 
 
sudo chkconfig docker on  
将Docker安装到CentOS上后，你需要将自己添加到docker群组，那样才能以非root用户的身份来运行Docker。为此，使用这个命令：

sudo usermod -a -G docker $USER  
退出，重新登录，以激活群组变更。

至此，你应该能够以非特权用户的身份来运行docker命令了。

（三）

列出所有的image

$ docker images 
运行Container

$ docker run --name shell -i -t ubuntu:latest /bin/bash 
 
$ docker run -t -i efd1e7457182 /bin/bash 
两个参数，-t表示给容器tty终端，-i表示可以interactive，可以交互。

退出

$ exit 
编写Dockerfile，运行docker build指令，就可以构建自己的Image

Dockerfile提供了CMD和ENTRYPOINT这2个指令，允许你指定一个Image启动时的默认命令。CMD和ENTRYPOINT的区别是CMD的参数可以由docker run指令指定的参数覆盖，而ENTRYPOINT则不可以。

使用Dockerfile创建image:

$ sudo docker build -t "sloan/centos-latest:v4" . 
其中-t标记添加tag,指定新的镜像的用户信息。 "."Dockerfile所有的路径。

修改image的tag:

$ sudo docker tag e5b5df13b85e sloan/centos-latest 
 
$ sudo docker images sloan/centos-latest 
上传镜像：

$ sudo docker push sloan/centos-latest 
保存Container到images

docker commit -a="sloan" -p=true -m="mongodb dir" e2e2e75ac08d 

参考：
http://cloud.51cto.com/art/201412/460142.htm
