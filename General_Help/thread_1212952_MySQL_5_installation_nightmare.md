---
title: "MySQL 5 installation nightmare"
date: 2009-07-14
forum: General Help
---

### Post by nr0mx on 2009-07-14
To cut a long frustrating despairing story short, I now have a MySQL 5 installation, but without the /etc/mysql/my.cnf file ( yes I deleted it in a moment of madness ). 
Turns out, mysql-server deb package reinstalls do not generate this file. Also, I've heard it whispered on the internets that you can get this from the source package. 
Running sudo apt-get source mysql-server gives me this:
E: Unable to find a source package for mysql-dfsg-5.0

The question: Which repository has the source package, any idea why it is not included by default ?  

Appreciate any help .. it'll go some way in turning this disaster of a day around. 

Also appreciate if anyone knows a command to check if a file ( say my.cnf ) exists in any package without installing said package(s) ?

---

### Post by Zeratul021 on 2009-07-14
In similar case I did apt-get remove the mysql-common and mysql-server package with --purge option to remove configs and then installed them again and whole directory structure was renewed.

---

### Post by nr0mx on 2009-07-14
> **Zeratul021 said:**
> In similar case I did apt-get remove the mysql-common and mysql-server package with --purge option to remove configs and then installed them again and whole directory structure was renewed.

How did you remove the mysql-common package ? I can't remove it without apt-get wanting to remove a ton of other dependent packages as well ..

---

### Post by nr0mx on 2009-07-14
> **nr0mx said:**
> How did you remove the mysql-common package ? I can't remove it without apt-get wanting to remove a ton of other dependent packages as well ..

Ok, tried this. Didn't work! In fact, it borked my MySQL install worse than before. 

Any suggestions ? I'm really running out of ideas here. Everywhere I look it's all voodoo magic; no answers. 

I'm not having a go at you; just a lament on general state of affairs and venting my frustration. 

Linux distros, in the last 5-10 years, have started to look ultra glitzy smooth things, but have the same issues plaguing them underneath the surface. I understand why this is, but that's scant comfort at times like these. 

I consider myself reasonably good with computers. I ran my first linux system in the days of red hat 3.5. I knew it was a challenge using linux then and I was prepared for it. In these days of fancy package management and nifty GUI interfaces, you kinda take installations for granted and then something like this hits you in the gut. :lolflag: Serves me right I guess ..

```

$ sudo aptitude install mysql-server
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information       
Initialising package states... Done
Writing extended state information... Done
The following NEW packages will be installed:
  mysql-server 
The following partially installed packages will be configured:
  mysql-server-5.0 
0 packages upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B/57.2kB of archives. After unpacking 98.3kB will be used.
Writing extended state information... Done
Selecting previously deselected package mysql-server.
(Reading database ... 189642 files and directories currently installed.)
Unpacking mysql-server (from .../mysql-server_5.1.30really5.0.75-0ubuntu10.2_all.deb) ...
 * Stopping MySQL database server mysqld                                                     [ OK ] 
Setting up mysql-server-5.0 (5.1.30really5.0.75-0ubuntu10.2) ...
 * Stopping MySQL database server mysqld                                                     [ OK ] 
 * Reloading AppArmor profiles ...                                                           [ OK ] 
 * Starting MySQL database server mysqld                                                     [fail] 
invoke-rc.d: initscript mysql, action "start" failed.
dpkg: error processing mysql-server-5.0 (--configure):
 subprocess post-installation script returned error exit status 1
dpkg: dependency problems prevent configuration of mysql-server:
 mysql-server depends on mysql-server-5.0; however:
  Package mysql-server-5.0 is not configured yet.
dpkg: error processing mysql-server (--configure):
 dependency problems - leaving unconfigured
No apport report written because the error message indicates its a followup error from a previous failure.
      Errors were encountered while processing:
 mysql-server-5.0
 mysql-server
E: Sub-process /usr/bin/dpkg returned an error code (1)
A package failed to install.  Trying to recover:
Setting up mysql-server-5.0 (5.1.30really5.0.75-0ubuntu10.2) ...
 * Stopping MySQL database server mysqld                                                     [ OK ] 
090714 16:03:08 [Warning] Can't create test file /var/db/mysql/hailstorm.lower-test
090714 16:03:08 [Warning] Can't create test file /var/db/mysql/hailstorm.lower-test
ERROR: 1146  Table 'mysql.user' doesn't exist
090714 16:03:08 [ERROR] Aborting

090714 16:03:08 [Note] /usr/sbin/mysqld: Shutdown complete

 * Reloading AppArmor profiles ...                                                           [ OK ] 
 * Starting MySQL database server mysqld                                                                                                                                                    [fail]
invoke-rc.d: initscript mysql, action "start" failed.
dpkg: error processing mysql-server-5.0 (--configure):
 subprocess post-installation script returned error exit status 1
dpkg: dependency problems prevent configuration of mysql-server:
 mysql-server depends on mysql-server-5.0; however:
  Package mysql-server-5.0 is not configured yet.
dpkg: error processing mysql-server (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 mysql-server-5.0
 mysql-server
Reading package lists... Done             
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initialising package states... Done
Writing extended state information... Done



```

---

### Post by Zeratul021 on 2009-07-15
Well what I did was:
1) stop the server
2) uninstall mysql common and server packages with purge
3) install them again


seem that you dpkg is having trouble configuring it maybe try runing apt-get autoclean and autoremove to clean the garbage and and look with aptitude search mysql what from mysql universe remained installed on your system.

gl

---

