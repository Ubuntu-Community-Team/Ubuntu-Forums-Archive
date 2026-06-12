---
title: "broken mysql"
date: 2009-07-06
forum: General Help
---

### Post by johnh10000 on 2009-07-06
Hi I seem to have managed to install mysql twice!!!  yep tried to remove it with the usual, here the responce:

(Reading database ... 151005 files and directories currently installed.)
Removing db4.6-util ...
Removing libapache2-mod-bt ...
Removing libbttracker0 ...
Removing libbtutil0 ...
Removing libswfdec-0.8-0 ...
Removing mysql-server-5.0 ...
 * Stopping MySQL database server mysqld                                 [fail] 
invoke-rc.d: initscript mysql, action "stop" failed.
dpkg: error processing mysql-server-5.0 (--remove):
 subprocess pre-removal script returned error exit status 1
 * Stopping MySQL database server mysqld                                 [fail] 
invoke-rc.d: initscript mysql, action "stop" failed.
 * Starting MySQL database server mysqld                                 [ OK ] 
/usr/bin/mysqladmin: connect to server at 'localhost' failed
error: 'Access denied for user 'debian-sys-maint'@'localhost' (using password: YES)'
Processing triggers for man-db ...
Processing triggers for libc6 ...
ldconfig deferred processing now taking place
Errors were encountered while processing:
 mysql-server-5.0
E: Sub-process /usr/bin/dpkg returned an error code (1)
johnh10000@tux:~$

Use `dselect' or `aptitude' for user-friendly package management.
johnh10000@tux:~$ sudo dpkg -P mysql-server
dpkg - warning: ignoring request to remove mysql-server which isn't installed.
johnh10000@tux:~$ mysql
ERROR 1045 (28000): Access denied for user 'johnh10000'@'localhost' (using password: NO)
johnh10000@tux:~$

---

### Post by cpetercarter on 2009-07-06
I guess that you had mysql running as a service at the time you were trying to remove it. Perhaps you need to stop the mysqld server before trying to remove it.

---

### Post by johnh10000 on 2009-07-06
> **cpetercarter said:**
> I guess that you had mysql running as a service at the time you were trying to remove it. Perhaps you need to stop the mysqld server before trying to remove it.

stopped everything mysql ... and
/usr/bin/mysqladmin: connect to server at 'localhost' failed
error: 'Access denied for user 'debian-sys-maint'@'localhost' (using password: YES)'

---

