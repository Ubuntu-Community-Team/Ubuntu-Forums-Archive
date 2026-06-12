---
title: "msyql: how to really, really remove it?"
date: 2011-05-23
forum: General Help
---

### Post by sanderj on 2011-05-23
Hi,

How can I really, really remove everything related to mysql / mysql-server.

I read and tried all kinds of things, but on every reinstall there is still old mysql stuff there, for example an existing password. Even resetting the password does not help.

Reason of removal: it looks like the mysql setup is really corrupt, so I want to remove, and then do a fresh install.

Running Ubuntu 11.04 64-bit

Help appreciated


sander@R540:~$ sudo apt-get purge mysql-server
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package mysql-server is not installed, so not removed
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
1 not fully installed or removed.
After this operation, 0 B of additional disk space will be used.
debconf: DbDriver "config": /var/cache/debconf/config.dat is locked by another process: Resource temporarily unavailable
Setting up mysql-server-5.1 (5.1.54-1ubuntu4) ...
debconf: DbDriver "config": /var/cache/debconf/config.dat is locked by another process: Resource temporarily unavailable
dpkg: error processing mysql-server-5.1 (--configure):
 subprocess installed post-installation script returned error exit status 1
Errors were encountered while processing:
 mysql-server-5.1
E: Sub-process /usr/bin/dpkg returned an error code (1)
sander@R540:~$



sander@R540:~$ sudo dpkg --configure -a
Setting up mysql-server-5.1 (5.1.54-1ubuntu4) ...
debconf: DbDriver "config": /var/cache/debconf/config.dat is locked by another process: Resource temporarily unavailable
dpkg: error processing mysql-server-5.1 (--configure):
 subprocess installed post-installation script returned error exit status 1
Errors were encountered while processing:
 mysql-server-5.1
sander@R540:~$ 


sander@R540:~$ sudo dpkg --configure -a
Setting up mysql-server-5.1 (5.1.54-1ubuntu4) ...
110523 15:12:01 [Note] Plugin 'FEDERATED' is disabled.
110523 15:12:01  InnoDB: Initializing buffer pool, size = 8.0M
110523 15:12:01  InnoDB: Completed initialization of buffer pool
110523 15:12:01  InnoDB: Started; log sequence number 0 44233
110523 15:12:01  InnoDB: Starting shutdown...
110523 15:12:06  InnoDB: Shutdown completed; log sequence number 0 44233
start: Job failed to start
invoke-rc.d: initscript mysql, action "start" failed.
dpkg: error processing mysql-server-5.1 (--configure):
 subprocess installed post-installation script returned error exit status 1
Errors were encountered while processing:
 mysql-server-5.1
sander@R540:~$

---

### Post by Dave_L on 2011-05-23
My understanding is that "apt-get purge" will not remove configuration/settings files in in the users' home directories, for example, /home/USER/.my.ini, /root/.my.ini.  Those must be manually deleted.

---

### Post by sanderj on 2011-05-23
> **Dave_L said:**
> My understanding is that "apt-get purge" will not remove configuration/settings files in in the users' home directories, for example, /home/USER/.my.ini, /root/.my.ini.  Those must be manually deleted.

And do you know how I can remove things scattered around the disk?


sander@R540:~$ sudo rm -rf /etc/dbconfig-common/zabbix-server-mysql.conf
[sudo] password for sander: 
sander@R540:~$ sudo rm -rf /etc/logrotate.d/zabbix-server-mysql
sander@R540:~$ sudo rm -rf /usr/share/dbconfig-common/data/zabbix-server-mysql

---

### Post by sanderj on 2011-05-26
After a few days of trying out different methods from posts elsewhere, it seems mysql is running: no more errors. 
Alas, I can't tell what exactly solved the problem, so here some snippets from my history

```

  582  sudo dpkg -S etc/mysql
  583  sudo apt-get update
  584  sudo apt-get upgrade
  585  sudo aptitude purge mysql-server
  586  sudo apt-get purge mysql-server
  587  sudo aptitude install mysql-server
  588  sudo apt-get install mysql-server
  589  sudo apt-get install mysql-server-5.1
  590  sudo apt-get autoremove --purge mysql-server mysql-server
  591  sudo apt-get install mysql-server 
  592  cd /etc/mysql/ 
  593  ll
  594  sudo touch my.cnf
  595  sudo dpkg --configure -a



  604  sudo mysql_install_db
  605  sudo mysqld_safe --user=mysql &



```

---

### Post by sanderj on 2011-05-27
Some more info, hopefully useful:

I got this error message:

```
Unable to connect to database: Unable to connect to MySQL server: Can't connect to local MySQL server through socket '/var/run/mysqld/mysqld.sock' (111)

```


To check whether mysql is running:

```
sander@R540:~$ ps -ef | grep -i mys
mysql     9976     1  0 14:08 ?        00:00:00 /usr/sbin/mysqld --user=mysql
sander   10701  9619  0 14:42 pts/2    00:00:00 grep --color=auto -i mys
sander@R540:~$
```

The above show mysqld running (as user mysql)

If *not*, try this: becomre root, and start mysqld


```
root@R540:~# mysqld --user=mysql
110527 13:53:07 [Note] Plugin 'FEDERATED' is disabled.
110527 13:53:08  InnoDB: Initializing buffer pool, size = 8.0M
110527 13:53:08  InnoDB: Completed initialization of buffer pool
110527 13:53:08  InnoDB: Started; log sequence number 0 276948
110527 13:53:08 [Note] Event Scheduler: Loaded 0 events
110527 13:53:08 [Note] mysqld: ready for connections.
Version: '5.1.54-1ubuntu4'  socket: '/var/run/mysqld/mysqld.sock'  port: 3306  (Ubuntu)

```

Then try to access the database again. Hopefully it works. To stop it again, CTRL-C didn't work for me, so I close the terminal, and then issued "sudo service mysql stop"


The root cause was in /etc/init/mysql.conf. In that file, I changed

```
exec /usr/sbin/mysqld 

```

into:

```

exec /usr/sbin/mysqld --user=mysql

```

... to let mysqld start under user account mysql. That solved it for me: the database was accessible, also after reboots.

---

