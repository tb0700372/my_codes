# <center>自动化运维(上)--- 基本命令操作以及部署Djang商城项目</center>

---

>## 一、服务器连接

SSH

* ssh `username`@`IP`
* 示例
    ```bash
    $ ssh -i "/Users/rooteng/Desktop/CsdnPython/Teng.pem" ubuntu@ec2-18-191-127-195.us-east-2.compute.amazonaws.com  # SSH 连接
    >>>
    Welcome to Ubuntu 16.04.4 LTS (GNU/Linux 4.4.0-1062-aws x86_64)

    * Documentation:  https://help.ubuntu.com
    * Management:     https://landscape.canonical.com
    * Support:        https://ubuntu.com/advantage

    Get cloud support with Ubuntu Advantage Cloud Guest:
        http://www.ubuntu.com/business/services/cloud

    33 packages can be updated.
    0 updates are security updates.

    Last login: Fri Aug  3 11:12:03 2018 from 183.192.28.152
    ubuntu@ip-172-31-16-33:~$ who
    ubuntu   pts/0        2018-08-08 10:56 (183.192.31.1)
    ubuntu@ip-172-31-16-33:~$ pwd
    /home/ubuntu
    ```

>## 二、环境部署

更新源

* apt update
* apt list --upgradable
* apt install -y vim

<p style="padding-right:50%"></p>

* 示例
    ```bash
    ubuntu@ip-172-31-16-33:~$ sudo su
    root@ip-172-31-16-33:/home/ubuntu# apt update
    Hit:1 http://us-east-2.ec2.archive.ubuntu.com/ubuntu xenial InRelease
    Get:2 http://us-east-2.ec2.archive.ubuntu.com/ubuntu xenial-updates InRelease [109 kB]
    Get:3 http://us-east-2.ec2.archive.ubuntu.com/ubuntu xenial-backports InRelease [107 kB]
    Get:4 http://us-east-2.ec2.archive.ubuntu.com/ubuntu xenial-updates/main amd64 Packages [825 kB]
    Get:5 http://security.ubuntu.com/ubuntu xenial-security InRelease [107 kB]
    Get:6 http://us-east-2.ec2.archive.ubuntu.com/ubuntu xenial-updates/universe amd64 Packages [679 kB]
    Fetched 1,826 kB in 0s (3,047 kB/s)
    Reading package lists... Done
    Building dependency tree
    Reading state information... Done
    38 packages can be upgraded. Run 'apt list --upgradable' to see them.
    root@ip-172-31-16-33:/home/ubuntu# apt list --upgradable
    Listing... Done
    apt/xenial-updates 1.2.27 amd64 [upgradable from: 1.2.26]
    apt-transport-https/xenial-updates 1.2.27 amd64 [upgradable from: 1.2.26]
    apt-utils/xenial-updates 1.2.27 amd64 [upgradable from: 1.2.26]
    base-files/xenial-updates 9.4ubuntu4.7 amd64 [upgradable from: 9.4ubuntu4.6]
    bsdutils/xenial-updates 1:2.27.1-6ubuntu3.6 amd64 [upgradable from: 1:2.27.1-6ubuntu3.4]
    cloud-init/xenial-updates 18.3-9-g2e62cb8a-0ubuntu1~16.04.2 all [upgradable from: 18.2-4-g05926e48-0ubuntu1~16.04.2]
    grub-legacy-ec2/xenial-updates 18.3-9-g2e62cb8a-0ubuntu1~16.04.2 all [upgradable from: 18.2-4-g05926e48-0ubuntu1~16.04.2]
    libapt-inst2.0/xenial-updates 1.2.27 amd64 [upgradable from: 1.2.26]
    libapt-pkg5.0/xenial-updates 1.2.27 amd64 [upgradable from: 1.2.26]
    libblkid1/xenial-updates 2.27.1-6ubuntu3.6 amd64 [upgradable from: 2.27.1-6ubuntu3.4]
    libdrm-common/xenial-updates 2.4.91-2~16.04.1 all [upgradable from: 2.4.83-1~16.04.1]
    libdrm2/xenial-updates 2.4.91-2~16.04.1 amd64 [upgradable from: 2.4.83-1~16.04.1]
    libfdisk1/xenial-updates 2.27.1-6ubuntu3.6 amd64 [upgradable from: 2.27.1-6ubuntu3.4]
    libglib2.0-0/xenial-updates 2.48.2-0ubuntu4 amd64 [upgradable from: 2.48.2-0ubuntu1]
    libglib2.0-data/xenial-updates 2.48.2-0ubuntu4 all [upgradable from: 2.48.2-0ubuntu1]
    libmount1/xenial-updates 2.27.1-6ubuntu3.6 amd64 [upgradable from: 2.27.1-6ubuntu3.4]
    libpam-systemd/xenial-updates 229-4ubuntu21.4 amd64 [upgradable from: 229-4ubuntu21.2]
    libslang2/xenial-updates 2.3.0-2ubuntu1.1 amd64 [upgradable from: 2.3.0-2ubuntu1]
    libsmartcols1/xenial-updates 2.27.1-6ubuntu3.6 amd64 [upgradable from: 2.27.1-6ubuntu3.4]
    libsystemd0/xenial-updates 229-4ubuntu21.4 amd64 [upgradable from: 229-4ubuntu21.2]
    libudev1/xenial-updates 229-4ubuntu21.4 amd64 [upgradable from: 229-4ubuntu21.2]
    libuuid1/xenial-updates 2.27.1-6ubuntu3.6 amd64 [upgradable from: 2.27.1-6ubuntu3.4]
    linux-aws/xenial-updates 4.4.0.1063.65 amd64 [upgradable from: 4.4.0.1062.64]
    linux-headers-aws/xenial-updates 4.4.0.1063.65 amd64 [upgradable from: 4.4.0.1062.64]
    linux-image-aws/xenial-updates 4.4.0.1063.65 amd64 [upgradable from: 4.4.0.1062.64]
    mount/xenial-updates 2.27.1-6ubuntu3.6 amd64 [upgradable from: 2.27.1-6ubuntu3.4]
    python-apt-common/xenial-updates 1.1.0~beta1ubuntu0.16.04.2 all [upgradable from: 1.1.0~beta1ubuntu0.16.04.1]
    python3-apt/xenial-updates 1.1.0~beta1ubuntu0.16.04.2 amd64 [upgradable from: 1.1.0~beta1ubuntu0.16.04.1]
    shared-mime-info/xenial-updates 1.5-2ubuntu0.2 amd64 [upgradable from: 1.5-2ubuntu0.1]
    snapd/xenial-updates 2.34.2 amd64 [upgradable from: 2.32.9]
    squashfs-tools/xenial-updates 1:4.3-3ubuntu2.16.04.2 amd64 [upgradable from: 1:4.3-3ubuntu2.16.04.1]
    systemd/xenial-updates 229-4ubuntu21.4 amd64 [upgradable from: 229-4ubuntu21.2]
    systemd-sysv/xenial-updates 229-4ubuntu21.4 amd64 [upgradable from: 229-4ubuntu21.2]
    ubuntu-core-launcher/xenial-updates 2.34.2 amd64 [upgradable from: 2.32.9]
    udev/xenial-updates 229-4ubuntu21.4 amd64 [upgradable from: 229-4ubuntu21.2]
    update-notifier-common/xenial-updates 3.168.9 all [upgradable from: 3.168.8]
    util-linux/xenial-updates 2.27.1-6ubuntu3.6 amd64 [upgradable from: 2.27.1-6ubuntu3.4]
    uuid-runtime/xenial-updates 2.27.1-6ubuntu3.6 amd64 [upgradable from: 2.27.1-6ubuntu3.4]
    ```

### 1. Python

    * apt install -y python3
    * apt install -y python3-pip

    * 示例
        ```bash
        $ python
        Python 3.6.4 |Anaconda, Inc.| (default, Jan 16 2018, 12:04:33)
        [GCC 4.2.1 Compatible Clang 4.0.1 (tags/RELEASE_401/final)] on darwin
        Type "help", "copyright", "credits" or "license" for more information.
        >>> import this
        The Zen of Python, by Tim Peters

        Beautiful is better than ugly.
        Explicit is better than implicit.
        Simple is better than complex.
        Complex is better than complicated.
        Flat is better than nested.
        Sparse is better than dense.
        Readability counts.
        Special cases aren't special enough to break the rules.
        Although practicality beats purity.
        Errors should never pass silently.
        Unless explicitly silenced.
        In the face of ambiguity, refuse the temptation to guess.
        There should be one-- and preferably only one --obvious way to do it.
        Although that way may not be obvious at first unless you're Dutch.
        Now is better than never.
        Although never is often better than *right* now.
        If the implementation is hard to explain, it's a bad idea.
        If the implementation is easy to explain, it may be a good idea.
        Namespaces are one honking great idea -- let's do more of those!
        >>>exit()
        ```

### 2. Djang&Uwsgi

    * pip3 install django==1.11.13
    * pip3 install uwsgi

    * 示例

    ```bash
    # django安装
    root@localhost:/home/teng# pip3 install django==1.11.13
    Collecting django==1.11.13
    .....
    Installing collected packages: pytz, django
    Successfully installed django-1.11.13 pytz-2018.5

    # uwsgi安装
    root@localhost:/home/teng# pip3 install uwsgi
    Collecting uwsgi
    .....
    Successfully built uwsgi
    Installing collected packages: uwsgi
    Successfully installed uwsgi-2.0.17.1

    # django 项目创建
    root@localhost:/home/teng# mkdir test
    root@localhost:/home/teng# cd test/
    root@localhost:/home/teng/test# django-admin startproject demo
    root@localhost:/home/teng/test# cd demo/
    root@localhost:/home/teng/test/demo# cd demo/
    root@localhost:/home/teng/test/demo# python3 manage.py startapp index
    root@localhost:/home/teng/test/demo# vi index/views.py
    ...
        1 from django.shortcuts import render
        2 from django.http import HttpResponse
        3
        4 # Create yur views here.
        5 def index(request):
        6     return HttpResponse("Hello!!")
    ...
    root@localhost:/home/teng/test/demo# vi index/urls.py
    ...
    1 from django.conf.urls import url
    2
    3 from . import views
    4
    5 urlpatterns = [
    6     url(r'^$', views.index, name='index'),
    7 ]
    ...

    root@localhost:/home/teng/test/demo# vi demo/urls.py
    ...
    16 from django.conf.urls import include,url
    17 from django.contrib import admin
    18
    19 urlpatterns = [
    20     url(r'^admin/', admin.site.urls),
    21     url(r'^index/', include('index.urls')),
    22 ]
    ...
    root@localhost:/home/teng/test/demo# vi demo/settings.py
    ...
    ALLOWED_HOSTS = ["*"]
    ...

    ```

#### 2.1 Django运行项目

    ```bash
    root@localhost:/home/teng/test/demo# python3 manage.py runserver 0:8000
    ```
    ![img01][img01]

#### 2.2 Uwsgi运行项目

    ```bash
    # 开启
    root@localhost:/home/teng/test/demo# uwsgi --http :9090 --chdir /home/teng/test/demo --module demo.wsgi

    # 结束
    root@localhost:/home/teng/test/demo# ps -ef | grep uwsgi
    root     24801 16322  0 10:09 pts/0    00:00:00 grep --color=auto uwsgi
    root@localhost:/home/teng/test/demo# kill -9 16322
    ```
    ![img02][img02]

### 3. AB

    ```bash
    # 安装
    apt install apache2-utils
    # 测试
    ab -c 20 -n 10000 http://192.168.1.9/
    ```

    <div class="line_2">
        <div>

    ```bash
    # django
    root@localhost:/home/teng# ab -c 20 -n 10000 http://192.168.1.9/
    This is ApacheBench, Version 2.3 <$Revision: 1807734 $>
    Copyright 1996 Adam Twiss, Zeus Technology Ltd, http://www.zeustech.net/
    Licensed to The Apache Software Foundation, http://www.apache.org/

    Benchmarking 192.168.1.9 (be patient)
    Completed 1000 requests
    Completed 2000 requests
    Completed 3000 requests
    Completed 4000 requests
    Completed 5000 requests
    Completed 6000 requests
    Completed 7000 requests
    Completed 8000 requests
    Completed 9000 requests
    Completed 10000 requests
    Finished 10000 requests

    Server Software:        WSGIServer/0.2
    Server Hostname:        192.168.1.9
    Server Port:            80

    Document Path:          /
    Document Length:        7 bytes

    Concurrency Level:      20
    Time taken for tests:   118.942 seconds
    Complete requests:      10000
    Failed requests:        0
    Total transferred:      1890000 bytes
    HTML transferred:       70000 bytes
    Requests per second:    84.07 [#/sec] (mean)
    Time per request:       237.883 [ms] (mean)
    Time per request:       11.894 [ms] (mean, across all concurrent requests)
    Transfer rate:          15.52 [Kbytes/sec] received

    Connection Times (ms)
                min  mean[+/-sd] median   max
    Connect:        0   30 214.0      0    3004
    Processing:     7  208 129.4    164    2753
    Waiting:        4  189 128.0    144    2729
    Total:          7  237 249.3    171    5373

    Percentage of the requests served within a certain time (ms)
    50%    171
    66%    243
    75%    287
    80%    315
    90%    399
    95%    486
    98%   1104
    99%   1146
    100%   5373 (longest request)
    ```

        </div>
        <div>

    ```bash
    # uwsgi
    root@localhost:/home/teng# ab -c 20 -n 10000 http://192.168.1.9/
    This is ApacheBench, Version 2.3 <$Revision: 1807734 $>
    Copyright 1996 Adam Twiss, Zeus Technology Ltd, http://www.zeustech.net/
    Licensed to The Apache Software Foundation, http://www.apache.org/

    Benchmarking 192.168.1.9 (be patient)
    Completed 1000 requests
    Completed 2000 requests
    Completed 3000 requests
    Completed 4000 requests
    Completed 5000 requests
    Completed 6000 requests
    Completed 7000 requests
    Completed 8000 requests
    Completed 9000 requests
    Completed 10000 requests
    Finished 10000 requests

    Server Software:
    Server Hostname:        192.168.1.9
    Server Port:            80

    Document Path:          /
    Document Length:        7 bytes

    Concurrency Level:      20
    Time taken for tests:   17.488 seconds
    Complete requests:      10000
    Failed requests:        0
    Total transferred:      1140000 bytes
    HTML transferred:       70000 bytes
    Requests per second:    571.82 [#/sec] (mean)
    Time per request:       34.976 [ms] (mean)
    Time per request:       1.749 [ms] (mean, across all concurrent requests)
    Transfer rate:          63.66 [Kbytes/sec] received

    Connection Times (ms)
                    min  mean[+/-sd] median   max
    Connect:        0    0   0.6      0      15
    Processing:    13   34   8.3     34      95
    Waiting:       11   34   8.3     34      94
    Total:         13   35   8.3     35      99

    Percentage of the requests served within a certain time (ms)
        50%     35
        66%     39
        75%     40
        80%     41
        90%     45
        95%     48
        98%     51
        99%     53
        100%     99 (longest request)
    ```

        </div>
    </div>

### 4. Nginx

    ```bash
    apt install -y nginx       # 安装
    nginx -v                   # 查看版本
    service nginx start        # 启动服务
    service nginx restart      # 重启服务
    service nginx stop         # 停止服务
    vi /etc/nginx/nginx.conf   # 配置文件
    nginx -s reload            # 重新读取
    ```

    ```bash
    # 安装
        apt install -y nginx
        root@localhost:/home/teng# nginx -v
        nginx version: nginx/1.14.0 (Ubuntu)
        root@localhost:/home/teng# service nginx start
        * Starting nginx nginx                                                  [ OK ]
        root@localhost:/home/teng# service nginx restart
        * Restarting nginx nginx                                                [ OK ]
        root@localhost:/home/teng# service nginx stop
        * Stopping nginx nginx                                                  [ OK ]
        root@localhost:/home/teng#
    ```

### 5. MemCached

    ```bash
    apt install -y memcached      # 安装
    service memcached stop        # 停止
    service memcached start       # 启动
    service memcached restart     # 重启
    vi /etc/memcached.conf        # 配置
    ```

### 6. RabbitMQ

    ```bash
    apt install -y rabbitmq-server                          # 安装
    rabbitmq-plugins enable rabbitmq_management             # -安装
    service rabbitmq-server start                           # 启动
    rabbitmqctl add_user teng root                          # 添加用户
    rabbitmqctl delete_user teng#                           # 删除用户
    rabbitmqctl set_user_tags teng administrator            # 设置用户角色
    rabbitmqctl set_permissions -p / teng ".*" ".*" ".*"    # 设置用户权限
    pip3 install pika                                       # Python
    pip3 install celery                                     # python
    vi web.py                                               # 设置
    ```

### 7. Mysql

    ```bash
    apt install -y mysql-server mysql-client  # 安装
    service mysql start                       # 启动
    service mysql restart                     # 重启
    service mysql stop                        # 停止
    pip3 install                              # python
    ```

>## 三、商城项目部署

* 准备
    ```bash
    # 传输项目文件到服务器
    scp -i "/Users/rooteng/Desktop/CsdnPython/Teng.pem" myobject.zip ubuntu@ec2-18-191-127-195.us-east-2.compute.amazonaws.com:/home/ubuntu
    unzip myobject.zip                                                                          # 解压项目
    CREATE DATABASE IF NOT EXISTS shopdb DEFAULT CHARACTER SET utf8 COLLATE utf8_general_ci;    # 创建数据库
    mysql -u root -p shopdb < shopdb.sql                                                        # 恢复数据库
    python3 manage.py runserver 0:8000                                                          # 启动项目
    ```

    ![img03][img03]

>## 基本练习

### 文件操作

```bash
创建
复制
移动
编辑
搜索
链接
打包
权限
删除
```

* 创建
    ```bash
    root@localhost:/home/teng/aa# mkdir aaa
    root@localhost:/home/teng/aa# ls
    aaa
    root@localhost:/home/teng/aa# touch aa.txt
    root@localhost:/home/teng/aa# ls
    aa.txt  aaa
    root@localhost:/home/teng/aa# vi bb.txt
    root@localhost:/home/teng/aa# ls
    aa.txt  aaa  bb.txt
    root@localhost:/home/teng/aa#
    ```
* 复制
    ```bash
    root@localhost:/home/teng/aa# cp aa.txt aa1.txt
    root@localhost:/home/teng/aa# ls
    aa.txt  aa1.txt  aaa  bb.txt
    root@localhost:/home/teng/aa# cp -r aaa aaa1
    root@localhost:/home/teng/aa# ls
    aa.txt  aa1.txt  aaa  aaa1  bb.txt
    root@localhost:/home/teng/aa#
    ```
* 移动
    ```bash
    root@localhost:/home/teng/aa# mv aa.txt aaa
    root@localhost:/home/teng/aa# ls
    aa1.txt  aaa  aaa1  bb.txt
    root@localhost:/home/teng/aa# mv aaa/aa.txt aa.txt
    root@localhost:/home/teng/aa# ls
    aa.txt  aa1.txt  aaa  aaa1  bb.txt
    root@localhost:/home/teng/aa# cd aaa
    root@localhost:/home/teng/aa/aaa# ls
    root@localhost:/home/teng/aa/aaa# cd ..
    root@localhost:/home/teng/aa# ls
    aa.txt  aa1.txt  aaa  aaa1  bb.txt
    root@localhost:/home/teng/aa# mv aa1.txt aa2.txt
    root@localhost:/home/teng/aa# ls
    aa.txt  aa2.txt  aaa  aaa1  bb.txt
    ```
* 编辑
    ```bash
    vi aa.txt         # 编辑文件
    vim aa.txt        # 编辑文件
    cat aa.txt        # 编辑文件
    head -n 5 aa.txt  # 查看文件头5行
    tail -n 5 aa.txt  # 查看文件末尾五行
    tail -f aa.txt    # 监视文件
    ```
* 搜索
    ```bash
    root@localhost:/home/teng/aa# find /home -name *a
    /home/teng/aa/aaa
    ```
* 链接
    ```bash
    root@localhost:/home/teng/aa# ls
    aa.txt  aa2.txt  aaa  aaa1  bb.txt
    ln -s aa.txt aa3.txt     # (创建软链接)
    ln bb.txt bb3.txt        # (创建硬链接)
    root@localhost:/home/teng/aa# ls
    aa.txt  aa2.txt  aa3.txt  aaa  aaa1  bb.txt  bb3.txt
    ```
* 打包
    ```bash
    # 打包
    root@localhost:/home/teng/aa# ls
    aa1  aaa  aaa1  bb3.txt
    root@localhost:/home/teng/aa# tar -zcvf test.tar.gz aaa
    aaa/
    aaa/aa.txt
    aaa/aa2.txt
    aaa/aa3.txt
    root@localhost:/home/teng/aa# tar -cjf test2.bz2 aa1
    root@localhost:/home/teng/aa# zip a.zip aaa
    root@localhost:/home/teng/aa# ls
    a.zip aa1  aaa  aaa1  bb3.txt  test.tar.gz  test2.bz2

    # 解包
    root@localhost:/home/teng/aa# ls
    a.zip  aa1  bb3.txt  test.tar.gz  test2.bz2
    root@localhost:/home/teng/aa#  tar -zxvf test.tar.gz
    aaa/
    aaa/aa.txt
    aaa/aa2.txt
    aaa/aa3.txt
    root@localhost:/home/teng/aa# tar -xjf test2.bz2
    root@localhost:/home/teng/aa# unzip a.zip
    Archive:  a.zip
    root@localhost:/home/teng/aa# ls
    a.zip  aa1  aaa  bb3.txt  test.tar.gz  test2.bz2
    ```
* 权限
    ```bash
    root@localhost:/home/test# ls -l
    -rw-r--r--. 1 root root 0 Aug  9 13:33 1.py
    -rw-r--r--. 1 jack ubb  0 Aug  9 13:38 jack.txt
    -rw-r--r--. 1 rose uaa  0 Aug  9 13:38 rose.txt

    root@localhost:/home/test# chmod 777 1.py
    root@localhost:/home/test# chown jack rose.txt
    root@localhost:/home/test# chown rose jack.txt
    root@localhost:/home/test# chgrp ubb rose.txt
    root@localhost:/home/test# chgrp uaa jack.txt
    root@localhost:/home/test# ls -l
    -rwxrwxrwx. 1 root root 0 Aug  9 13:33 1.py
    -rw-r--r--. 1 rose uaa  0 Aug  9 13:38 jack.txt
    -rw-r--r--. 1 jack ubb  0 Aug  9 13:38 rose.txt
    ```
* 删除
    ```bash
    root@localhost:/home/test# rm 1.py
    root@localhost:/home/test# rm jack.txt
    root@localhost:/home/test# rm rose.txt
    root@localhost:/home/test# ls
    ```

### 用户

```bash
用户组
新建
修改密码
删除
```

* 用户组
    ```bash
    root@localhost:/home/teng/aa# groupadd uaa
    root@localhost:/home/teng/aa# groupadd ubb
    ```

* 新建
    ```bash
    root@localhost:/home/teng/aa# useradd -g uaa -m rose
    root@localhost:/home/teng/aa# useradd -g ubb -m jack
    ```

* 修改密码
    ```bash
    root@localhost:/home/teng/aa# passwd rose
    Enter new UNIX password:
    Retype new UNIX password:
    passwd: password updated successfully
    root@localhost:/home/teng/aa# passwd jack
    Enter new UNIX password:
    Retype new UNIX password:
    passwd: password updated successfully
    ```

* 删除
    ```bash
    userdel jack -r
    userdel rose -r
    ```

```bash
$ ssh rose@192.168.1.9
rose@192.168.1.9's password:
Welcome to Ubuntu 18.04 LTS (GNU/Linux 3.10.84-gfcc38b5-04605-g0488a9c aarch64)

 * Documentation:  https://help.ubuntu.com
 * Management:     https://landscape.canonical.com
 * Support:        https://ubuntu.com/advantage


The programs included with the Ubuntu system are free software;
the exact distribution terms for each program are described in the
individual files in /usr/share/doc/*/copyright.

Ubuntu comes with ABSOLUTELY NO WARRANTY, to the extent permitted by
applicable law.

Ubuntu 18.04 LTS [running via Linux Deploy]

$ ssh jack@192.168.1.9
jack@192.168.1.9's password:
Welcome to Ubuntu 18.04 LTS (GNU/Linux 3.10.84-gfcc38b5-04605-g0488a9c aarch64)

 * Documentation:  https://help.ubuntu.com
 * Management:     https://landscape.canonical.com
 * Support:        https://ubuntu.com/advantage

The programs included with the Ubuntu system are free software;
the exact distribution terms for each program are described in the
individual files in /usr/share/doc/*/copyright.

Ubuntu comes with ABSOLUTELY NO WARRANTY, to the extent permitted by
applicable law.

Ubuntu 18.04 LTS [running via Linux Deploy]
```

### 进程

```bash
ps -ef               # 进程System风格显示
ps -ef | grep httpd  # 筛选进程
ps aux               # 进程BSD风格显示
top                  # 进程表
kill                 # 结束进程id -9 强制结束
pkill                # 结束进程名

```

### 空间

```bash
root@localhost:/home/test# df -h
Filesystem                              Size  Used Avail Use% Mounted on
/dev/block/bootdevice/by-name/userdata   55G  8.8G   46G  17% /
tmpfs                                   1.8G  580K  1.8G   1% /dev
tmpfs                                   1.9G     0  1.9G   0% /dev/shm

//查看系统中文件的使用情况
df -h
//查看当前目录下各个文件及目录占用空间大小
du -sh *
```

# -END-
