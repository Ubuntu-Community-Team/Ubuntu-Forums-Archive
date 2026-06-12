---
title: "ERROR 1006 (HY000): Can't create database"
date: 2011-03-13
forum: General Help
---

### Post by mhoy06 on 2011-03-13
Was not sure which forum to post in. My search for my error showed a post in this forum.

[PHP]#mysql -u root -pPassWord
mysql> create database whatever;
ERROR 1006 (HY000): Can't create database 'whatever' (errno: 13)
mysql> [/PHP]

Searching around I found a site that says the following:

[PHP]# chown -R root:mysql /usr/local/mysql
# chown -R mysql:mysql /usr/local/mysql/data[/PHP]

/usr/local does not have a mysql folder
There is a mysql in /usr/share
but no data folder in /usr/share/mysql

Can anyone tell me what I need to do? I just installed mysql-server on this machine.

I am using:
Server version: 5.0.75-0ubuntu10.5 (Ubuntu)

Ubuntu 9.04 Jaunty

---

### Post by hai2lp on 2011-03-13
are you sure you put the data dir in /usr/local/mysql/data  

because ubuntu by default put the data dir in /var/lib/mysql

you could open /etc/mysql/my.cnf

and see the datadir

---

### Post by mhoy06 on 2011-03-13
> **hai2lp said:**
> are you sure you put the data dir in /usr/local/mysql/data  

because ubuntu by default put the data dir in /var/lib/mysql

you could open /etc/mysql/my.cnf

and see the datadir


[PHP]/etc/mysql/my.cnf:

datadir        = /var/lib/mysql

#cd /var/lib/mysql[/PHP]

no data directory here there is another mysql directory but it also does not have a data directory

---

### Post by hai2lp on 2011-03-13
> **mhoy06 said:**
> [PHP]/etc/mysql/my.cnf:

datadir        = /var/lib/mysql

#cd /var/lib/mysql[/PHP]

no data directory here there is another mysql directory but it also does not have a data directory


Well you should do 

```
sudo mkdir /var/lib/mysql/
```
  
[HTML]sudo chown -R mysql:mysql /var/lib/mysql/[/HTML]

---

