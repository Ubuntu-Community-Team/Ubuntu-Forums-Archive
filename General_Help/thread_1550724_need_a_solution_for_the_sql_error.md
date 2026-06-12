---
title: "need a solution for the sql error"
date: 2010-08-11
forum: General Help
---

### Post by rahulburra on 2010-08-11
hello everyone

when i try to **start my sql server in ubuntu 9.10 box** with the help of the command 
[B]
/etc/init.d/mysql restart
[/B]
[B]i get an error message as below
[/B]
100713  1:51:23 [Warning] Can't create test file /nsm/mysql/ubuntu.lower-test
100713  1:51:23 [Warning] Can't create test file /nsm/mysql/ubuntu.lower-test
100713  1:51:23 [ERROR] /usr/sbin/mysqld: Can't find file: './mysql/user.frm' (errno: 13)
100713  1:51:23 [ERROR] /usr/sbin/mysqld: Can't find file: './mysql/user.frm' (errno: 13)
ERROR: 1017  Can't find file: './mysql/user.frm' (errno: 13)
100713  1:51:23 [ERROR] Aborting

100713  1:51:23 [Note] /usr/sbin/mysqld: Shutdown complete

 * Starting MySQL database server mysqld                                 [fail] 
invoke-rc.d: initscript mysql, action "start" failed.
dpkg: error processing mysql-server-5.0 (--configure):
 subprocess installed post-installation script returned error exit status 1
E: Sub-process /usr/bin/dpkg returned an error code (1)

can anyone please help me solve this problem it will be a great help in completing my project

Thankyou
RahulBurra

---

### Post by surfer on 2010-08-11
try

```

$ sudo service mysql start

```

you need to start the server with root privileges!

---

### Post by rahulburra on 2010-08-11
thnks for the quick reply
but when i try to run with the **root privilige using the above command**
i get an error as below

** * Starting MySQL database server mysqld                                 [fail] **
:(:(

---

### Post by hudsonl on 2010-08-11
> **rahulburra said:**
> hello everyone

when i try to **start my sql server in ubuntu 9.10 box** with the help of the command 
[B]
/etc/init.d/mysql restart
[/B]
[B]i get an error message as below
[/B]
100713  1:51:23 [Warning] Can't create test file /nsm/mysql/ubuntu.lower-test
100713  1:51:23 [Warning] Can't create test file /nsm/mysql/ubuntu.lower-test
100713  1:51:23 [ERROR] /usr/sbin/mysqld: Can't find file: './mysql/user.frm' (errno: 13)
100713  1:51:23 [ERROR] /usr/sbin/mysqld: Can't find file: './mysql/user.frm' (errno: 13)
ERROR: 1017  Can't find file: './mysql/user.frm' (errno: 13)
100713  1:51:23 [ERROR] Aborting

100713  1:51:23 [Note] /usr/sbin/mysqld: Shutdown complete

 * Starting MySQL database server mysqld                                 [fail] 
invoke-rc.d: initscript mysql, action "start" failed.
dpkg: error processing mysql-server-5.0 (--configure):
 subprocess installed post-installation script returned error exit status 1
E: Sub-process /usr/bin/dpkg returned an error code (1)

can anyone please help me solve this problem it will be a great help in completing my project

Thankyou
RahulBurra


Where is MySQL installed ?

Look at my.cnf file and look for the datadir 

> locate my.cnf
/etc/mysql/my.cnf
> vi (or gedit) /etc/mysql/my.cnf

The contents should look something like this:
user            = mysql
socket          = /var/run/mysqld/mysqld.sock
port            = 3306
basedir         = /usr
**datadir         = /var/lib/mysql**
tmpdir          = /tmp


Is the file system **/nsm/** mounted and available ?

Judging by the error ... there are permissions or the file system /nsm is not available ??

---

