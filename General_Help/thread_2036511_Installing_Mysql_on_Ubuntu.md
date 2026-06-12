---
title: "Installing Mysql on Ubuntu"
date: 2012-08-02
forum: General Help
---

### Post by tejas87 on 2012-08-02
Hello,

I recently tried to install mysql on ubuntu but gave me an error:
Sub-process /usr/bin/dpkg returned an error code (1)

---

### Post by spjackson on 2012-08-02
Welcome.

We could do with a bit more information in order to be able to help you.

Which version of Ubuntu are you using? How did you try to install it, e.g. via the Software Centre, Synaptic, apt-get?

Were there any other messages preceding the one you mention? If you didn't make a note, you could run it again and post the output in full.

One possible cause is if the root partition is full, but there are many other possibilities.

---

### Post by moonport on 2012-08-02
Are you using Synaptic or apt-get?

---

### Post by tejas87 on 2012-08-03
Hello spjackson and moonport,
I am using the latest version of Ubuntu 12.04 LTS. I am trying to install it via apt-get.  This is what I did and the output as well:

sudo apt-get install mysql-server
[sudo] password for tejas: 
Sorry, try again.
[sudo] password for tejas: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
mysql-server is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
2 not fully installed or removed.
After this operation, 0 B of additional disk space will be used.
Do you want to continue [Y/n]? y
Setting up mysql-server-5.5 (5.5.24-0ubuntu0.12.04.1) ...
120803 11:29:16 [Note] Plugin 'FEDERATED' is disabled.
120803 11:29:16 InnoDB: The InnoDB memory heap is disabled
120803 11:29:16 InnoDB: Mutexes and rw_locks use GCC atomic builtins
120803 11:29:16 InnoDB: Compressed tables use zlib 1.2.3.4
120803 11:29:16 InnoDB: Initializing buffer pool, size = 128.0M
120803 11:29:16 InnoDB: Completed initialization of buffer pool
120803 11:29:16 InnoDB: highest supported file format is Barracuda.
120803 11:29:17  InnoDB: Waiting for the background threads to start
120803 11:29:18 InnoDB: 1.1.8 started; log sequence number 1595675
120803 11:29:18  InnoDB: Starting shutdown...
120803 11:29:18  InnoDB: Shutdown completed; log sequence number 1595675
start: Job failed to start
invoke-rc.d: initscript mysql, action "start" failed.
dpkg: error processing mysql-server-5.5 (--configure):
 subprocess installed post-installation script returned error exit status 1
dpkg: dependency problems prevent configuration of mysql-server:
 mysql-server depends on mysql-server-5.5; however:
  Package mysql-server-5.5 is not configured yet.
dpkg: error processing mysql-server (--configure):
 dependency problems - leaving unconfigured
No apport report written because the error message indicates it's a follow-up error from a previous failure.
                            Errors were encountered while processing:
 mysql-server-5.5
 mysql-server
E: Sub-process /usr/bin/dpkg returned an error code (1)

---

### Post by jat421 on 2012-08-03
Try a clean un-install and then install again


apt-get –purge remove mysql-server
apt-get –purge remove mysql-client
apt-get –purge remove mysql-common apt-get autoremove
apt-get autoclean

---

### Post by tejas87 on 2012-08-03
Tried that method but no luck same error

---

### Post by vipulkumar7 on 2012-08-03
First you need to remove that mysql package completely Try this command

> 
sudo apt-get --purge remove mysql-server mysql-common mysql-client libmysqlclient15-dev libmysql-ruby

Then update it
> sudo apt-get update

Then install Msqlor Mysql server depends upon you what you want to install
> 
sudo apt-get mysql or mysql-server

i hop it will work :) :)

---

### Post by tejas87 on 2012-08-03
Thanks it worked

---

### Post by tejas87 on 2012-08-03
ok now that i have installed xampp. I tried localhost on web browser and the xampp page opens but when i open local host phpmyadmin i get a error.

 New XAMPP security concept:

Access to the requested directory is only available from the local network.

This setting can be configured in the file "httpd-xampp.conf".

---

