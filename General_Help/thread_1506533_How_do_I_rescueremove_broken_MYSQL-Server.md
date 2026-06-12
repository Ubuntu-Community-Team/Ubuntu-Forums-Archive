---
title: "How do I rescue/remove broken MYSQL-Server?"
date: 2010-06-10
forum: General Help
---

### Post by LG_Auction on 2010-06-10
I believe that 10.04 & MYSQL Server are not compatible. My problem is that I have not been able to remove MYSQL from the system. Every thing I've tried says I have to reinstall before removing and I can NOT get anything to update.

What can I do short of a hammer & chisel?

Thanks in advance.

---

### Post by apjone on 2010-06-10
From a terminal run 

```

sudo apt-get remove mysql-server

```

and post what it shows

---

### Post by GuiGuy on 2010-06-10
> **LG_Auction said:**
> I believe that 10.04 & MYSQL Server are not compatible. My problem is that I have not been able to remove MYSQL from the system. Every thing I've tried says I have to reinstall before removing and I can NOT get anything to update.

What can I do short of a hammer & chisel?

Thanks in advance.

I'm having difficulty as well. [See my post here]("http://ubuntuforums.org/showthread.php?t=1506743").

---

### Post by drdos2006 on 2010-06-10
MySQL-client update also borks my 9.10 64bit. The error message is to do with a pre-installation script for client 5.1, so it is MySQL and not Ubuntu causing the problem.

regards

---

### Post by LG_Auction on 2010-06-10
apjone,

You are a God! I think it is working now. Here is the output from the commands:

sudo apt-get remove mysql-server

E: dpkg was interrupted, you must manually run 'sudo dpkg --configure -a' to correct the problem.

sudo dpkg --configure -a 
Setting up libmysqlclient16 (5.1.41-3ubuntu12.3) ... 

Setting up mysql-server-core-5.1 (5.1.41-3ubuntu12.3) ... 
Setting up mysql-client-core-5.1 (5.1.41-3ubuntu12.3) ... 
Setting up libdbd-mysql-perl (4.012-1ubuntu1) ... 
Setting up mysql-client-5.1 (5.1.41-3ubuntu12.3) ... 
dpkg: error processing mysql-server-5.1 (--configure): 
 Package is in a very bad inconsistent state - you should 
 reinstall it before attempting configuration. 
Processing triggers for libc-bin ... 
ldconfig deferred processing now taking place 
Errors were encountered while processing: 
 mysql-server-5.1 


sudo apt-get remove mysql-server 
Reading package lists... Done 
Building dependency tree       
Reading state information... Done 
Package mysql-server is not installed, so not removed 
The following packages were automatically installed and are no longer required: 
  linux-headers-2.6.32-21 mysql-gui-tools-common 
  linux-headers-2.6.32-21-generic 
Use 'apt-get autoremove' to remove them. 
The following extra packages will be installed: 
  mysql-server-5.1 
Suggested packages: 
  tinyca mailx 
The following packages will be upgraded: 
  mysql-server-5.1 
1 upgraded, 0 newly installed, 0 to remove and 0 not upgraded. 
1 not fully installed or removed. 
Need to get 0B/7,008kB of archives. 
After this operation, 0B of additional disk space will be used. 
Do you want to continue [Y/n]? y 
Preconfiguring packages ... 
(Reading database ... 165271 files and directories currently installed.) 
Preparing to replace mysql-server-5.1 5.1.41-3ubuntu12.1 (using .../mysql-server-5.1_5.1.41-3ubuntu12.3_i386.deb) ... 
mysql stop/waiting 
Unpacking replacement mysql-server-5.1 ... 
Processing triggers for ureadahead ... 
ureadahead will be reprofiled on next reboot 
Processing triggers for man-db ... 
Setting up mysql-server-5.1 (5.1.41-3ubuntu12.3) ... 
mysql start/running, process 2193 

Processing triggers for libc-bin ... 
ldconfig deferred processing now taking place

---

### Post by apjone on 2010-06-10
Glad I could point you in the right direction!

---

### Post by GuiGuy on 2010-06-10
> **drdos2006 said:**
> MySQL-client update also borks my 9.10 64bit. The error message is to do with a pre-installation script for client 5.1, so it is MySQL and not Ubuntu causing the problem.

regards

Sorry, disagree. mysql is part of the ubuntu distro and update system. Ergo, it is a Ubuntu problem. 
.

---

### Post by GuiGuy on 2010-06-10
> **LG_Auction said:**
> apjone,

You are a God! I think it is working now. Here is the output from the commands:

sudo apt-get remove mysql-server

This has really turned out a PITA for me. 

> ~$ sudo apt-get remove mysql-server 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  libhtml-template-perl mysql-server-5.1
Use 'apt-get autoremove' to remove them.
The following extra packages will be installed:
  mysql-server-5.1
Suggested packages:
  tinyca mailx
The following packages will be REMOVED:
  mysql-server
The following packages will be upgraded:
  mysql-server-5.1
1 upgraded, 0 newly installed, 1 to remove and 0 not upgraded.
1 not fully installed or removed.
Need to get 0B/7,103kB of archives.
After this operation, 127kB disk space will be freed.
Do you want to continue [Y/n]? yes
Preconfiguring packages ...
(Reading database ... 221770 files and directories currently installed.)
Preparing to replace mysql-server-5.1 5.1.41-3ubuntu12.1 (using .../mysql-server-5.1_5.1.41-3ubuntu12.3_amd64.deb) ...


.. at this point it hangs. I cannot even kill apt. I have to reboot :(

What to do? Cannot remove it. Cannot upgrade it. Cannot fix it. Cannot re-install it. 

What a pain.

---

### Post by qbox on 2010-06-12
Same s**t different day for me. I try apt-get autoremove, i try to remove packages one by one ... nothing helps.... If some one find solution I will buy him a beer ;)

---

### Post by java.artisan on 2010-06-12
I'm adding a kilo of Belgian chocolate to the reward.

Sadly I have had the same story yesterday. No way to reinstall mysql server after I've uninstalled it. I'm probably going to reinstall the OS and put in big letters on the desktop NOT to uninstall mysql.

I thought reinstallation-resistent software was windows' prerogative. Congratulations to the author at Oracle ! ](*,)

Another workaround is probably to install mysql server in a virtualbox. And access this from the broken host os. But there's probably a catch somewhere... that's oracle software too. :mrgreen:

---

### Post by GuiGuy on 2010-06-12
> **qbox said:**
> Same s**t different day for me. I try apt-get autoremove, i try to remove packages one by one ... nothing helps.... If some one find solution I will buy him a beer ;)

See my [thread here]("http://ubuntuforums.org/showthread.php?t=1506743"). Worked for me..

---

### Post by java.artisan on 2010-06-12
For me it didn't. In the end I removed everything. my.cnf and all. 

Nothing left to comment out ... :-)

---

### Post by Rhiknow on 2010-07-05
Any resolution to this?

I'm trying to install a bog standard mysql-server

sudo apt-get install mysql-server

It hangs at this point:

Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following extra packages will be installed:
  libdbd-mysql-perl libdbi-perl libhtml-template-perl libmysqlclient16 libnet-daemon-perl libplrpc-perl mysql-client-5.1 mysql-client-core-5.1 mysql-common
  mysql-server-5.1 mysql-server-core-5.1
Suggested packages:
  dbishell libipc-sharedcache-perl tinyca mailx
The following NEW packages will be installed
  libdbd-mysql-perl libdbi-perl libhtml-template-perl libmysqlclient16 libnet-daemon-perl libplrpc-perl mysql-client-5.1 mysql-client-core-5.1 mysql-common
  mysql-server mysql-server-5.1 mysql-server-core-5.1
0 upgraded, 12 newly installed, 0 to remove and 1 not upgraded.
Need to get 0B/24.3MB of archives.
After this operation, 60.9MB of additional disk space will be used.
Do you want to continue [Y/n]? Y
Preconfiguring packages ...
Selecting previously deselected package mysql-common.
(Reading database ... 51786 files and directories currently installed.)
Unpacking mysql-common (from .../mysql-common_5.1.41-3ubuntu12.3_all.deb) ...
Selecting previously deselected package libnet-daemon-perl.
Unpacking libnet-daemon-perl (from .../libnet-daemon-perl_0.43-1_all.deb) ...
Selecting previously deselected package libplrpc-perl.
Unpacking libplrpc-perl (from .../libplrpc-perl_0.2020-2_all.deb) ...
Selecting previously deselected package libdbi-perl.
Unpacking libdbi-perl (from .../libdbi-perl_1.609-1build1_amd64.deb) ...
Selecting previously deselected package libmysqlclient16.
Unpacking libmysqlclient16 (from .../libmysqlclient16_5.1.41-3ubuntu12.3_amd64.deb) ...
Selecting previously deselected package libdbd-mysql-perl.
Unpacking libdbd-mysql-perl (from .../libdbd-mysql-perl_4.012-1ubuntu1_amd64.deb) ...
Selecting previously deselected package mysql-client-core-5.1.
Unpacking mysql-client-core-5.1 (from .../mysql-client-core-5.1_5.1.41-3ubuntu12.3_amd64.deb) ...
Selecting previously deselected package mysql-client-5.1.
Unpacking mysql-client-5.1 (from .../mysql-client-5.1_5.1.41-3ubuntu12.3_amd64.deb) ...
Selecting previously deselected package mysql-server-core-5.1.
Unpacking mysql-server-core-5.1 (from .../mysql-server-core-5.1_5.1.41-3ubuntu12.3_amd64.deb) ...
Processing triggers for man-db ...
Setting up mysql-common (5.1.41-3ubuntu12.3) ...
Selecting previously deselected package mysql-server-5.1.
(Reading database ... 52151 files and directories currently installed.)
Unpacking mysql-server-5.1 (from .../mysql-server-5.1_5.1.41-3ubuntu12.3_amd64.deb) ...
Selecting previously deselected package libhtml-template-perl.
Unpacking libhtml-template-perl (from .../libhtml-template-perl_2.9-1_all.deb) ...
Selecting previously deselected package mysql-server.
Unpacking mysql-server (from .../mysql-server_5.1.41-3ubuntu12.3_all.deb) ...
Processing triggers for ureadahead ...
Processing triggers for man-db ...
Setting up libnet-daemon-perl (0.43-1) ...
Setting up libplrpc-perl (0.2020-2) ...
Setting up libdbi-perl (1.609-1build1) ...
Setting up libmysqlclient16 (5.1.41-3ubuntu12.3) ...

Setting up libdbd-mysql-perl (4.012-1ubuntu1) ...
Setting up mysql-client-core-5.1 (5.1.41-3ubuntu12.3) ...
Setting up mysql-client-5.1 (5.1.41-3ubuntu12.3) ...
Setting up mysql-server-core-5.1 (5.1.41-3ubuntu12.3) ...
Setting up mysql-server-5.1 (5.1.41-3ubuntu12.3) ...  <<<Hang here>>>



I did an apt-get update and an apt-get autoremove before I started. I even did 
rm -rf /var/lib/mysql/
rm -rf /var/log/mysql
rm -rf /etc/mysql/

and removed the mysql user. All to no avail.

Any ideas?

---

### Post by java.artisan on 2010-07-05
I've got it PARTIALLY fixed : The permissions on files somewhere in /var/lib/mysql were wrong.

chown -R mysql.mysql /var/lib/mysql made it possible to start the database manually with "sudo mysqld_safe --user mysql".


Unfortunately the startup service still doesn't work: 

start mysql => "Start: Unknown job: mysql".

---

### Post by Rhiknow on 2010-07-05
Thanks for that update...

This is an absolute disaster...

Came across this stuff (seemingly the MySQL guys have fixed it, but it's not in the packages yet):
[https://bugs.launchpad.net/null/+bug/551097](https://bugs.launchpad.net/null/+bug/551097)
[https://bugs.launchpad.net/ubuntu/+source/mysql-dfsg-5.1/+bug/551130](https://bugs.launchpad.net/ubuntu/+source/mysql-dfsg-5.1/+bug/551130)

Still trying...

Keep getting:
ERROR 2002 (HY000): Can't connect to local MySQL server through socket '/var/run/mysqld/mysqld.sock
when I try to run `mysql -u root -p`

How long will it take for a new version of mysql-server to hit Synaptic? Can I install an unstable version for now, if so, how?

---

### Post by jdieter on 2010-07-06
PLEASE does anyone have a solution for ERROR 2002 (HY000): Can't connect to local MySQL server through socket '/var/run/mysqld/mysqld.sock'
Can I go back to a previous version or something?
There must be some way to fix this? It worked fine until the first time I rebooted.

---

### Post by chjustc on 2010-08-23
Hi there,

Has there been an solution for this problem?

I also have the same problem. The output from sudo apt-get autoremove && sudo apt-get autoclean is as follows

Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be REMOVED:
  mysql-server-5.1
0 upgraded, 0 newly installed, 1 to remove and 61 not upgraded.
1 not fully installed or removed.
After this operation, 15.7MB disk space will be freed.
Do you want to continue [Y/n]? y
dpkg: error processing mysql-server-5.1 (--remove):
 Package is in a very bad inconsistent state - you should
 reinstall it before attempting a removal.
Errors were encountered while processing:
 mysql-server-5.1
E: Sub-process /usr/bin/dpkg returned an error code (1)
chenj@chenj-desktop:~$ sudo apt-get remove mysql-server
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package mysql-server is not installed, so not removed
The following packages were automatically installed and are no longer required:
  mysql-server-5.1
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 62 not upgraded.
1 not fully installed or removed.
Need to get 0B/7,103kB of archives.
After this operation, 0B of additional disk space will be used.
Preconfiguring packages ...
Selecting previously deselected package mysql-server-5.1.
(Reading database ... 203997 files and directories currently installed.)
Preparing to replace mysql-server-5.1 5.1.41-3ubuntu12.3 (using .../mysql-server-5.1_5.1.41-3ubuntu12.3_amd64.deb) ...

---

### Post by java.artisan on 2010-08-29
No news from my side. :-(

I coped with changing the ownership of /etc/mysql/... to "mysql" and start/stop the server on command line.

Now I've reinstalled kubuntu and it works completely again. Which is no solution whatsoever for a real database server...

---

### Post by chjustc on 2010-08-29
I fixed it without reinstalling ubuntu. The solution that worked for me is from [https://bugs.launchpad.net/ubuntu/+source/mysql-dfsg-5.1/+bug/613195](https://bugs.launchpad.net/ubuntu/+source/mysql-dfsg-5.1/+bug/613195)

The original reporter of the bug took the following steps:
1. I went to /etc/init and gave the command:
sudo gedit mysql.conf so that I could comment out the start-on lines,
saved the file and rebooted the computer.

2. I then cleared up package manager with: sudo dpkg --configure -a

3. I then used: sudo apt-get install --reinstall mysql-server

4. Next I used: sudo apt-get remove mysql-server

5. And then finally: sudo apt-get autoremove

6. After a reboot I was able to completely use update-manager.

I took the same steps and they worked. MySQL also worked fine.

---

### Post by shane.ramey on 2010-10-21
Try 'apt-get remove mysql-server-5.1' as well as a 'dpkg --purge mysql-server-5.1'

---

