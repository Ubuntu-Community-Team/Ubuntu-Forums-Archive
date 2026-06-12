---
title: "PHP and MySQL not working together"
date: 2011-08-09
forum: General Help
---

### Post by possien on 2011-08-09
I am sure I have about everything wacked out by now.  I have Ubuntu 11.04 installed.  I can see my apache server on localhost and use php scripts.  I have mysql running but can't associate mysql with php.  I have tried about every tutorial I could find but no success.  phpinfo shows no mysql.

Any help would be appreciated.

---

### Post by fdrake on 2011-08-09
> **possien said:**
> I am sure I have about everything wacked out by now.  I have Ubuntu 11.04 installed.  I can see my apache server on localhost and use php scripts.  I have mysql running but can't associate mysql with php.  I have tried about every tutorial I could find but no success.  phpinfo shows no mysql.

Any help would be appreciated.

```

mysql -V
php -v

```
post the results

---

### Post by possien on 2011-08-09
* mysql-client-core-5.1
 * mysql-cluster-client-5.1

PHP 5.3.5-1ubuntu7.2 with Suhosin-Patch (cli) (built: May  2 2011 23:00:17) 
Copyright (c) 1997-2009 The PHP Group
Zend Engine v2.3.0, Copyright (c) 1998-2010 Zend Technologies

---

### Post by Wim Sturkenboom on 2011-08-09
I think you need *_php5-mysql_* to get that working; it is in the repositories.

---

### Post by Wim Sturkenboom on 2011-08-09
> **salemeni said:**
> Hi
If you use a local database, you need mysql-server
Thanks

You're right; maybe the below put me on the wrong track ;)
> **possien said:**
> ...I have mysql running...

---

### Post by possien on 2011-08-09
It appears somewhere I have a mysql server see below.

I have ran this (several times): apt-get install php5-mysql.

I get this: sudo apt-get install php5-mysql
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following extra packages will be installed:
  libmysqlclient16
The following packages will be REMOVED:
  mysql-cluster-client-5.1 mysql-cluster-server-5.1
The following NEW packages will be installed:
  libmysqlclient16 php5-mysql
0 upgraded, 2 newly installed, 2 to remove and 1 not upgraded.
Need to get 0 B/1,945 kB of archives.
After this operation, 76.5 MB disk space will be freed.
Do you want to continue [Y/n]? y
(Reading database ... 187427 files and directories currently installed.)
Removing mysql-cluster-server-5.1 ...
 * Stopping MySQL database server mysqld                                 [fail] 
invoke-rc.d: initscript mysql, action "stop" failed.
dpkg: error processing mysql-cluster-server-5.1 (--remove):
 subprocess installed pre-removal script returned error exit status 1
 * Stopping MySQL database server mysqld                                 [fail] 
invoke-rc.d: initscript mysql, action "stop" failed.
 * Starting MySQL database server mysqld                                 [ OK ] 
dpkg: mysql-cluster-client-5.1: dependency problems, but removing anyway as you requested:
 mysql-cluster-server-5.1 depends on mysql-cluster-client-5.1.
Removing mysql-cluster-client-5.1 ...
Processing triggers for man-db ...
Processing triggers for libc-bin ...
ldconfig deferred processing now taking place
Errors were encountered while processing:
 mysql-cluster-server-5.1
E: Sub-process /usr/bin/dpkg returned an error code (1)


I initially ran this:

apt-get install php5-mysql php5-curl php5-gd php5-idn php-pear php5-imagick php5-imap php5-mcrypt php5-memcache php5-ming php5-ps php5-pspell php5-recode php5-snmp php5-sqlite php5-tidy php5-xmlrpc php5-xsl

---

### Post by Wim Sturkenboom on 2011-08-09
Try to manually stop the mysql server; that seems to be the problem (from your output).

PS
Please place output between [noparse]```
 and 
```[/noparse]; easier to read ;)

---

### Post by possien on 2011-08-09
> **Wim Sturkenboom said:**
> Try to manually stop the mysql server; that seems to be the problem (from your output).

PS
Please place output between [noparse]```
 and 
```[/noparse]; easier to read ;)

Thanks, I removed all of mysql packages and reinstalled using Synaptic.  It appears that I had installed mysql-cluster-*server&client and was conflicting with the correct server/client.

Now, to figure out how to get into phpmyadmin.

So, I think we can close this one.

Thanks!

---

### Post by fdrake on 2011-08-09
```

sudo apt-get purge *mysql*
sudo apt-get purge *php*
<download attachment>
sudo chmod x apache_php.sh 
sudo ./apache_php.sh 

```

this commands will delete all previous mysql and php installs (to make sure there are no interferences) and it will install all the neccesaries pakages cgi, ssl, php5 mysql phpmyadmin etc.. at ones

---

### Post by Wim Sturkenboom on 2011-08-10
> **possien said:**
> So, I think we can close this one.

Thanks!Just mark the thread as solved using the thread tools just above the first post.

---

