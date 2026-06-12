---
title: "Latest update borks mysql-server"
date: 2010-06-10
forum: General Help
---

### Post by GuiGuy on 2010-06-10
I (stupidly) allowed an update to run (Lucid), knowing full well that something will break, as it always does <sigh>;

Anyway, I get this

> 
dpkg: error processing mysql-server-5.1 (--configure):
 Package is in a very bad inconsistent state - you should
 reinstall it before attempting configuration.
dpkg: dependency problems prevent configuration of mysql-server:
 mysql-server depends on mysql-server-5.1; however:
  Package mysql-server-5.1 is not configured yet.
dpkg: error processing mysql-server (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 mysql-server-5.1
 mysql-server


The problem now is that it won't let me uninstall it, purge it, configure it etc. Whatever I attempt in relation to mysql-server the system seems to hang. 

The apt history log tells me 
> 
Start-Date: 2010-06-11  06:56:45
Upgrade: mysql-server-5.1 (5.1.41-3ubuntu12.1, 5.1.41-3ubuntu12.3)



This is the mysql error log
> 00611  7:01:40 [Note] Plugin 'FEDERATED' is disabled.
100611  7:01:41  InnoDB: Started; log sequence number 0 201192
100611  7:01:41 [ERROR] Can't start server: Bind on TCP/IP port: Cannot assign requested address
100611  7:01:41 [ERROR] Do you already have another mysqld server running on port: 3306 ?
100611  7:01:41 [ERROR] Aborting

100611  7:01:41  InnoDB: Starting shutdown...
100611  7:01:42  InnoDB: Shutdown completed; log sequence number 0 201192
100611  7:01:42 [Note] /usr/sbin/mysqld: Shutdown complete
[QUOTE]


UPDATE: trying apt-get results in

[QUOTE]
Preparing to replace mysql-server-5.1 5.1.41-3ubuntu12.1 (using .../mysql-server-5.1_5.1.41-3ubuntu12.3_amd64.deb) ...
stop: Job has already been stopped: mysql
stop: Job has already been stopped: mysql
invoke-rc.d: initscript mysql, action "stop" failed.
invoke-rc.d returned 1
There is a MySQL server running, but we failed in our attempts to stop it.
Stop it yourself and try again!
dpkg: error processing /var/cache/apt/archives/mysql-server-5.1_5.1.41-3ubuntu12.3_amd64.deb (--unpack):
 subprocess new pre-installation script returned error exit status 1


So, it says that mysql-server is running, which explains why can't do anything. But if I 

sudo service mysqls stop 

it tells me "Job has already been stopped"

What's going on?

---

### Post by HeirPixel on 2010-06-10
Have you tried a ***sudo apt-get autoremove && sudo apt-get autoclean*** just to see if it rectifies anything? Maybe there's something else in there clogging up the pipes...

---

### Post by GuiGuy on 2010-06-10
> **HeirPixel said:**
> Have you tried a ***sudo apt-get autoremove && sudo apt-get autoclean*** just to see if it rectifies anything? Maybe there's something else in there clogging up the pipes...

Yes. The installer hangs with the message
>  subprocess new pre-installation script returned error exit status 1


Update: So, I cannot update, remove, reinstall, fix, purge etc mysql-server - Looks like another clean install. Next geek to tell me how great Linux is will get a smack in the mouth!

---

### Post by GuiGuy on 2010-06-11
It shouldn't be so complicated... 
[https://bugs.launchpad.net/ubuntu/+source/dpkg/+bug/512096](https://bugs.launchpad.net/ubuntu/+source/dpkg/+bug/512096)

PS: After I sorted this out I got some BS about mysql losing its socks or some such... Anyway, edit /etc/mysql/my.cnf  and comment out 
#bind-address		=

PS: PS: Every day I begin to dislike linux's "features" just a little bit more. Running a modern desktop computer should not be this complicated.

---

