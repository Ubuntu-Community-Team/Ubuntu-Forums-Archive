---
title: "problems installing Apache2, phpmyadmin on Ubuntu 10.04"
date: 2011-11-03
forum: General Help
---

### Post by skeptical4life on 2011-11-03
problems installing Apache2, phpmyadmin Ubuntu on 10.04
Ubuntu 10.04; i386pc
I'm relatively new to Ubuntu and have spent days trying to install a local host so I can work on my Joomla 1.7.2 site (that I created in Windows) and have had several problems.
1. phpMyadmin isn't showing in www folder
2. Permissions issues re: phpMyadmin and mysql
3. When following install instructions <[http://www.youtube.com/watch?v=-mG8kgMHK2A](http://www.youtube.com/watch?v=-mG8kgMHK2A) > I get this error:
:~$ sudo apt-get install linapache2-mod-auth-mysql phpmyadmin
Reading package lists... Done
Building dependency tree
Reading state information... Done
E: Unable to locate package linapache2-mod-auth-mysql


More Info reported:
PHP Version 5.3.5-1ubuntu7.3

System Linux michael-Gateway-M520 2.6.38-12-generic #51-Ubuntu SMP Wed Sep 28 14:25:20 UTC 2011 i686
Build Date Oct 13 2011 21:55:18
Server API Apache 2.0 Handler
Virtual Directory Support disabled
Configuration File (php.ini) Path /etc/php5/apache2
Loaded Configuration File /etc/php5/apache2/php.ini
Scan this dir for additional .ini files /etc/php5/apache2/conf.d
Additional .ini files parsed /etc/php5/apache2/conf.d/gd.ini, /etc/php5/apache2/conf.d/imap.ini, /etc/php5/apache2/conf.d/mcrypt.ini, /etc/php5/apache2/conf.d/mysql.ini, /etc/php5/apache2/conf.d/mysqli.ini, /etc/php5/apache2/conf.d/pdo.ini, /etc/php5/apache2/conf.d/pdo_mysql.ini, /etc/php5/apache2/conf.d/suhosin.ini
PHP API 20090626
PHP Extension 20090626
Zend Extension 220090626
Zend Extension Build API220090626,NTS
PHP Extension Build API20090626,NTS
Debug Build no
Thread Safety disabled
Zend Memory Manager enabled
Zend Multibyte Support disabled
IPv6 Support enabled
Registered PHP Streams https, ftps, compress.zlib, compress.bzip2, php, file, glob, data, http, ftp, phar, zip
Registered Stream Socket Transports tcp, udp, unix, udg, ssl, sslv3, sslv2, tls
Registered Stream Filters zlib.*, bzip2.*, convert.iconv.*, string.rot13, string.toupper, string.tolower, string.strip_tags, convert.*, consumed, dechunk, mcrypt.*, mdecrypt.*


What should I do?

---

### Post by alco75 on 2011-11-03
How did you actually install LAMP in the first place? I would clean up the broken install, if you can. Then, I find the path of least resistance is to use **tasksel**.

Make sure **tasksel** is actually installed:

```
sudo apt-get install tasksel
```

Then install LAMP in one go:

```
sudo tasksel install lamp-server
```

This will install Apache, MySQL and PHP in all the right places. It works out-of-the-box. You can restart your web server with **sudo service apache2 restart**.

---

### Post by alco75 on 2011-11-03
You'll need to install **phpmyadmin** separately, after the above:

```
sudo apt-get install phpmyadmin
```

Having said that, I've just tried it on Oneiric and it wasn't immediately available on **localhost/phpmyadmin** and I'm not sure which configuration files need changing.

(I use a combination of command line tools and NetBeans integrated SQL query browser as I don't really like PMA.)

---

### Post by satanselbow on 2011-11-03
> **skeptical4life said:**
> 
3. When following install instructions <[http://www.youtube.com/watch?v=-mG8kgMHK2A](http://www.youtube.com/watch?v=-mG8kgMHK2A) > I get this error:
:~$ sudo apt-get install linapache2-mod-auth-mysql phpmyadmin
Reading package lists... Done
Building dependency tree
Reading state information... Done
E: Unable to locate package linapache2-mod-auth-mysql


You have a typo in the apt-get line - it should read:

```

sudo apt-get install apache2-mod-auth-mysql phpmyadmin

```

---

### Post by skeptical4life on 2011-11-03
Thanks responders. I tried your suggestions but to no avail:

:~$ sudo apt-get install tasksel
Reading package lists... Done
Building dependency tree       
Reading state information... Done
tasksel is already the newest version.
The following packages were automatically installed and are no longer required:
  php-fpdf courier-imap linux-headers-2.6.38-8 mysql-gui-tools-common
  libsqlite0 courier-pop expect courier-base mlock libc-client2007e webalizer
  linux-headers-2.6.38-8-generic courier-authlib-userdb courier-authlib
  php5-imap proftpd-basic libpq5 libphp-phpmailer courier-authdaemon
  php5-suhosin
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 2 not upgraded.
Step 2:
0:~$ sudo tasksel install lamp-server



Step 3:
:~$ sudo apt-get install phpmyadmin
Reading package lists... Done
Building dependency tree       
Reading state information... Done
phpmyadmin is already the newest version.
The following packages were automatically installed and are no longer required:
  php-fpdf courier-imap linux-headers-2.6.38-8 mysql-gui-tools-common
  libsqlite0 courier-pop expect courier-base mlock libc-client2007e webalizer
  linux-headers-2.6.38-8-generic courier-authlib-userdb courier-authlib
  php5-imap proftpd-basic libpq5 libphp-phpmailer courier-authdaemon
  php5-suhosin
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 2 not upgraded.

:~$ sudo apt-get install apache2-mod-auth-mysql phpmyadmin
Reading package lists... Done
Building dependency tree       

Modified Step 2:
Reading state information... Done
E: Unable to locate package apache2-mod-auth-mysql

---

### Post by satanselbow on 2011-11-03
Apologies :$

Should be ```
sudo apt-get install libapache2-mod-auth-mysql
```

---

### Post by skeptical4life on 2011-11-03
Thanks. 
:~$ sudo apt-get install libapache2-mod-auth-mysql
[sudo] password for XXXXXXX: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  php-fpdf courier-imap linux-headers-2.6.38-8 mysql-gui-tools-common
  libsqlite0 courier-pop expect courier-base mlock libc-client2007e webalizer
  linux-headers-2.6.38-8-generic courier-authlib-userdb courier-authlib
  php5-imap proftpd-basic libpq5 libphp-phpmailer courier-authdaemon
  php5-suhosin
Use 'apt-get autoremove' to remove them.
The following NEW packages will be installed
  libapache2-mod-auth-mysql
0 upgraded, 1 newly installed, 0 to remove and 2 not upgraded.
Need to get 25.9 kB of archives.
After this operation, 115 kB of additional disk space will be used.
Get:1 [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) natty/main libapache2-mod-auth-mysql i386 4.3.9-13ubuntu1 [25.9 kB]
Fetched 25.9 kB in 0s (169 kB/s)               
Selecting previously deselected package libapache2-mod-auth-mysql.
(Reading database ... 188912 files and directories currently installed.)
Unpacking libapache2-mod-auth-mysql (from .../libapache2-mod-auth-mysql_4.3.9-13ubuntu1_i386.deb) ...
Setting up libapache2-mod-auth-mysql (4.3.9-13ubuntu1) ...

Now what?

---

### Post by pavi_elex on 2011-11-03
Download new XAMPP folder. [http://sourceforge.net/projects/xampp/](http://sourceforge.net/projects/xampp/)

first stop your old lampp - /opt/lampp/lampp stop
now rename it to lampp_old and put new lampp folder in this place and start lampp - /opt/lampp/lampp start
and try to start phpmyadmin

if still there is problem. stop lampp and Try
sudo apt-get --purge remove mysql-server mysql-common mysql-client

sudo apt-get install mysql-server mysql-common mysql-client
sudo apt-get install apache2
sudo apt-get install php
sudo apt-get install php5-mysql
sudo apt-get install phpmyadmin

---

### Post by skeptical4life on 2011-11-03
Sorry it's not working and taking so long...

1. I downloaded xampp
2. entered command:
:~$ /opt/lampp/lampp stop
bash: /opt/lampp/lampp: No such file or directory

3. Then entered:
:~$ /opt/lampp/lampp stop
bash: /opt/lampp/lampp: No such file or directory
:~$ sudo apt-get --purge remove mysql-server mysql-common mysql-client
[sudo] password for XXXXXXX: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package mysql-client is not installed, so not removed
The following packages were automatically installed and are no longer required:
  php-fpdf courier-imap linux-headers-2.6.38-8 mysql-gui-tools-common
  libsqlite0 php5-gd wwwconfig-common courier-pop libmcrypt4 libjs-mootools
  expect courier-base mlock libc-client2007e webalizer
  linux-headers-2.6.38-8-generic courier-authlib-userdb courier-authlib
  php5-mcrypt php5-imap proftpd-basic javascript-common libpq5 dbconfig-common
  libphp-phpmailer courier-authdaemon php5-suhosin
Use 'apt-get autoremove' to remove them.
The following packages will be REMOVED
  libapache2-mod-auth-mysql* libdbd-mysql-perl* libmysqlclient16*
  libqt4-sql-mysql* mysql-client-5.1* mysql-client-core-5.1* mysql-common*
  mysql-server* mysql-server-5.1* mysql-server-core-5.1* php5-mysql*
  phpmyadmin*
0 upgraded, 0 newly installed, 12 to remove and 2 not upgraded.
After this operation, 70.0 MB disk space will be freed.
Do you want to continue [Y/n]? y
(Reading database ... 188917 files and directories currently installed.)
Removing libapache2-mod-auth-mysql ...
Module auth_mysql already disabled
Purging configuration files for libapache2-mod-auth-mysql ...
Removing mysql-server ...
Removing mysql-server-5.1 ...
mysql stop/waiting
Purging configuration files for mysql-server-5.1 ...
Removing mysql-client-5.1 ...
Removing libdbd-mysql-perl ...
Removing phpmyadmin ...
 * Reloading web server config apache2                                          apache2: Could not reliably determine the server's fully qualified domain name, using 127.0.1.1 for ServerName
                                                                         [ OK ]
Purging configuration files for phpmyadmin ...
 * Reloading web server config apache2                                          apache2: Could not reliably determine the server's fully qualified domain name, using 127.0.1.1 for ServerName
                                                                         [ OK ]
Removing php5-mysql ...
Purging configuration files for php5-mysql ...
Removing libqt4-sql-mysql ...
Removing mysql-server-core-5.1 ...
Removing mysql-client-core-5.1 ...
Removing libmysqlclient16 ...
Purging configuration files for libmysqlclient16 ...
Removing mysql-common ...
Purging configuration files for mysql-common ...
dpkg: warning: while removing mysql-common, directory '/etc/mysql' not empty so not removed.
Processing triggers for man-db ...
Processing triggers for ureadahead ...
ureadahead will be reprofiled on next reboot
Processing triggers for doc-base ...
Processing 1 removed doc-base file(s)...
Registering documents with dwww...
Registering documents with scrollkeeper...
Processing triggers for hicolor-icon-theme ...
Processing triggers for libapache2-mod-php5 ...
 * Reloading web server config apache2                                          apache2: Could not reliably determine the server's fully qualified domain name, using 127.0.1.1 for ServerName
                                                                         [ OK ]
Processing triggers for libc-bin ...
ldconfig deferred processing now taking place

Configuring phpmyadmin 

4. :~$ sudo apt-get install mysql-server mysql-common mysql-client
[sudo] password for XXXXXXX: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  php-fpdf courier-imap linux-headers-2.6.38-8 mysql-gui-tools-common
  libsqlite0 php5-gd wwwconfig-common courier-pop libmcrypt4 libjs-mootools
  expect courier-base mlock libc-client2007e webalizer
  linux-headers-2.6.38-8-generic courier-authlib-userdb courier-authlib
  php5-mcrypt php5-imap proftpd-basic javascript-common libpq5 dbconfig-common
  libphp-phpmailer courier-authdaemon php5-suhosin
Use 'apt-get autoremove' to remove them.
The following extra packages will be installed:
  libdbd-mysql-perl libmysqlclient16 mysql-client-5.1 mysql-client-core-5.1
  mysql-server-5.1 mysql-server-core-5.1
Suggested packages:
  tinyca
The following NEW packages will be installed
  libdbd-mysql-perl libmysqlclient16 mysql-client mysql-client-5.1
  mysql-client-core-5.1 mysql-common mysql-server mysql-server-5.1
  mysql-server-core-5.1
0 upgraded, 9 newly installed, 0 to remove and 2 not upgraded.
Need to get 0 B/21.6 MB of archives.
After this operation, 51.7 MB of additional disk space will be used.
Do you want to continue [Y/n]? y
Preconfiguring packages ...
Selecting previously deselected package mysql-common.
(Reading database ... 187688 files and directories currently installed.)
Unpacking mysql-common (from .../mysql-common_5.1.54-1ubuntu4_all.deb) ...
Selecting previously deselected package libmysqlclient16.
Unpacking libmysqlclient16 (from .../libmysqlclient16_5.1.54-1ubuntu4_i386.deb) ...
Selecting previously deselected package libdbd-mysql-perl.
Unpacking libdbd-mysql-perl (from .../libdbd-mysql-perl_4.016-1_i386.deb) ...
Selecting previously deselected package mysql-client-core-5.1.
Unpacking mysql-client-core-5.1 (from .../mysql-client-core-5.1_5.1.54-1ubuntu4_i386.deb) ...
Selecting previously deselected package mysql-client-5.1.
Unpacking mysql-client-5.1 (from .../mysql-client-5.1_5.1.54-1ubuntu4_i386.deb) ...
Selecting previously deselected package mysql-server-core-5.1.
Unpacking mysql-server-core-5.1 (from .../mysql-server-core-5.1_5.1.54-1ubuntu4_i386.deb) ...
Processing triggers for man-db ...
Setting up mysql-common (5.1.54-1ubuntu4) ...
Selecting previously deselected package mysql-server-5.1.
(Reading database ... 187885 files and directories currently installed.)
Unpacking mysql-server-5.1 (from .../mysql-server-5.1_5.1.54-1ubuntu4_i386.deb) ...
Selecting previously deselected package mysql-client.
Unpacking mysql-client (from .../mysql-client_5.1.54-1ubuntu4_all.deb) ...
Selecting previously deselected package mysql-server.
Unpacking mysql-server (from .../mysql-server_5.1.54-1ubuntu4_all.deb) ...
Processing triggers for ureadahead ...
Processing triggers for man-db ...
Setting up libmysqlclient16 (5.1.54-1ubuntu4) ...
Setting up libdbd-mysql-perl (4.016-1) ...
Setting up mysql-client-core-5.1 (5.1.54-1ubuntu4) ...
Setting up mysql-client-5.1 (5.1.54-1ubuntu4) ...
Setting up mysql-server-core-5.1 (5.1.54-1ubuntu4) ...
Setting up mysql-server-5.1 (5.1.54-1ubuntu4) ...
mysql start/running, process 4753
Setting up mysql-client (5.1.54-1ubuntu4) ...
Setting up mysql-server (5.1.54-1ubuntu4) ...
Processing triggers for libc-bin ...
ldconfig deferred processing now taking place

5. :~$ sudo apt-get install apache2
Reading package lists... Done
Building dependency tree       
Reading state information... Done
apache2 is already the newest version.
The following packages were automatically installed and are no longer required:
  php-fpdf courier-imap linux-headers-2.6.38-8 mysql-gui-tools-common
  libsqlite0 php5-gd wwwconfig-common courier-pop libmcrypt4 libjs-mootools
  expect courier-base mlock libc-client2007e webalizer
  linux-headers-2.6.38-8-generic courier-authlib-userdb courier-authlib
  php5-mcrypt php5-imap proftpd-basic javascript-common libpq5 dbconfig-common
  libphp-phpmailer courier-authdaemon php5-suhosin
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 2 not upgraded.

6. :~$ sudo apt-get install php
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to locate package php

7. :~$ sudo apt-get install php5-mysql
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  php-fpdf courier-imap linux-headers-2.6.38-8 mysql-gui-tools-common
  libsqlite0 php5-gd wwwconfig-common courier-pop libmcrypt4 libjs-mootools
  expect courier-base mlock libc-client2007e webalizer
  linux-headers-2.6.38-8-generic courier-authlib-userdb courier-authlib
  php5-mcrypt php5-imap proftpd-basic javascript-common libpq5 dbconfig-common
  libphp-phpmailer courier-authdaemon php5-suhosin
Use 'apt-get autoremove' to remove them.
The following NEW packages will be installed
  php5-mysql
0 upgraded, 1 newly installed, 0 to remove and 2 not upgraded.
Need to get 0 B/65.8 kB of archives.
After this operation, 250 kB of additional disk space will be used.
Selecting previously deselected package php5-mysql.
(Reading database ... 187970 files and directories currently installed.)
Unpacking php5-mysql (from .../php5-mysql_5.3.5-1ubuntu7.3_i386.deb) ...
Processing triggers for libapache2-mod-php5 ...
 * Reloading web server config apache2                                          apache2: Could not reliably determine the server's fully qualified domain name, using 127.0.1.1 for ServerName
                                                                         [ OK ]
Setting up php5-mysql (5.3.5-1ubuntu7.3) ...

8. :~$ sudo apt-get install phpmyadmin
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  php-fpdf courier-imap linux-headers-2.6.38-8 mysql-gui-tools-common
  libsqlite0 courier-pop expect courier-base mlock libc-client2007e webalizer
  linux-headers-2.6.38-8-generic courier-authlib-userdb courier-authlib
  php5-imap proftpd-basic libpq5 libphp-phpmailer courier-authdaemon
  php5-suhosin
Use 'apt-get autoremove' to remove them.
The following NEW packages will be installed
  phpmyadmin
0 upgraded, 1 newly installed, 0 to remove and 2 not upgraded.
Need to get 0 B/4,321 kB of archives.
After this operation, 17.8 MB of additional disk space will be used.
Preconfiguring packages ...
Selecting previously deselected package phpmyadmin.
(Reading database ... 187977 files and directories currently installed.)
Unpacking phpmyadmin (from .../phpmyadmin_4%3a3.3.10-1_all.deb) ...
Processing triggers for hicolor-icon-theme ...
Processing triggers for doc-base ...
Processing 1 added doc-base file(s)...
Registering documents with dwww...
Registering documents with scrollkeeper...
Processing triggers for man-db ...
Setting up phpmyadmin (4:3.3.10-1) ...
dbconfig-common: writing config to /etc/dbconfig-common/phpmyadmin.conf

Creating config file /etc/dbconfig-common/phpmyadmin.conf with new version

Creating config file /etc/phpmyadmin/config-db.php with new version
ERROR 1045 (28000): Access denied for user 'root'@'localhost' (using password: YES).
unable to connect to mysql server.
error encountered creating user:
ERROR 1045 (28000): Access denied for user 'root'@'localhost' (using password: YES)
dbconfig-common: phpmyadmin configure: trying again.
dbconfig-common: writing config to /etc/dbconfig-common/phpmyadmin.conf
Replacing config file /etc/phpmyadmin/config-db.php with new version
ERROR 1045 (28000): Access denied for user 'root'@'localhost' (using password: YES).
unable to connect to mysql server.
error encountered creating user:
ERROR 1045 (28000): Access denied for user 'root'@'localhost' (using password: YES)
dbconfig-common: phpmyadmin configure: aborted.
dbconfig-common: flushing administrative password
ERROR 1045 (28000): Access denied for user 'root'@'localhost' (using password: YES).
unable to connect to mysql server.
error encountered creating database:
ERROR 1045 (28000): Access denied for user 'root'@'localhost' (using password: YES)
dbconfig-common: phpmyadmin configure: aborted.
dbconfig-common: flushing administrative password
populating database via sql...  error encountered populating database:
mysql said: ERROR 1045 (28000): Access denied for user 'root'@'localhost' (using password: YES)
dbconfig-common: phpmyadmin configure: aborted.
dbconfig-common: flushing administrative password
done.
dbconfig-common: flushing administrative password
 * Reloading web server config apache2                                          apache2: Could not reliably determine the server's fully qualified domain name, using 127.0.1.1 for ServerName
  
Yikes now what???

---

### Post by pavi_elex on 2011-11-03
[CENTER]now put lampp folder in /opt and start lampp by 
$ sudo /opt/lampp/lampp start
[/CENTER]

---

### Post by alco75 on 2011-11-03
I would've thought it'd be better to just use tasksel really, as that installs the LAMP components where they're 'supposed' to be, rather than putting it in /opt and using xampp ...

---

### Post by satanselbow on 2011-11-03
Hey had to go to work but - gotta agree XAMPP on Linux is a poor solution.

I've not used XAMPP in many years, and only on windows so cannot help further. You may like it but the interface it supplies is clunky and intrusive.

---

### Post by skeptical4life on 2011-11-04
I can't move/copy lampp to /opt:
1. through terminal:
:~$ mv /michael/downloads/lampp /opt
mv: cannot stat `/michael/downloads/lampp': No such file or directory

:~$ sudo mv /michael/downloads/lampp /opt
[sudo] password for michael: 
mv: cannot stat `/michael/downloads/lampp': No such file or directory


2. through copy:
Error moving file: Permission denied
permissions for lampp = ok
permissions for /opt = you can not change the permissions, you are not the owner; owner 'root'

What am I doing wrong?

---

### Post by skeptical4life on 2011-11-07
1. Still no phpMyadmin in www folder
2. Can't log into phpMyadmin; error 1045: Can not log into Mysql server. Connection for controluser as defined in your configuration failed.

---

