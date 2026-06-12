---
title: "Mysql problem version 5.1"
date: 2009-11-23
forum: General Help
---

### Post by TheOneEyedMan on 2009-11-23
I keep getting an error when working trying to start MYSQL on my Karmic Koala Ubuntu 64:

ERROR 2002 (HY000): Can't connect to local MySQL server through socket '/var/run/mysqld/mysqld.sock' (2)

When I try to restart mysqld I get
/etc/init.d/mysql start
 * Starting MySQL database server mysqld                                   [fail]


I tried reinstalling the following packages and deleting my my.cnf file to no success
mysql-client
mysql-client-5.1
mysql-server-5.1


It used to work before my upgrade and now it does not. 

There is no file in /var/run/mysqld/ so the socket isn't appearing properly. 

That file doesn't seem to be anywhere I can find:
whereis mysqld.sock
mysqld: /usr/sbin/mysqld /usr/share/man/man8/mysqld.8.gz

ls -l /var/lib/mys*
total 4.0K
-rw-r--r-- 1 mysql mysql    0 2009-11-23 19:28 debian-5.1.flag
drwxr-xr-x 2 mysql mysql 4.0K 2009-11-23 19:10 mysql



Tried following the directions at <a href="http://ubuntuforums.org/showthread.php?t=665504&amp;highlight=mysql&amp;page=2">Re: mysql installation problem</a>  without success
[INDENT]sudo dpkg --configure -a
Setting up mysql-server-5.1 (5.1.37-1ubuntu5) ...
 * Stopping MySQL database server mysqld                                     [ OK ] 
 * Starting MySQL database server mysqld                                     [fail] 
invoke-rc.d: initscript mysql, action "start" failed.
dpkg: error processing mysql-server-5.1 (--configure):
 subprocess installed post-installation script returned error exit status 1
dpkg: dependency problems prevent configuration of mysql-server:
 mysql-server depends on mysql-server-5.1; however:
  Package mysql-server-5.1 is not configured yet.
dpkg: error processing mysql-server (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 mysql-server-5.1
 mysql-server[/INDENT]


Please help me out.

---

### Post by utkjamie on 2009-11-24
I had the same problem and found a solution that seems to be working for me here: [http://kubuntuforums.net/forums/index.php?topic=3108222.0](http://kubuntuforums.net/forums/index.php?topic=3108222.0)

Hope that helps!

---

