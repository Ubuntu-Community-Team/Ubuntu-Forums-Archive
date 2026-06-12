---
title: "Completely Remove MySql"
date: 2010-07-20
forum: General Help
---

### Post by finito on 2010-07-20
Sorry if this is in the wrong section.

This is the first time I have ever gotten so stumped while using Ubuntu.

I Installed the maintained package, Day one everything worked fine, I set a dummy database and work on it from VM windows. 

Day two weird errors, I searched around couldn't find the problem, the error was related to The root user losing privileges. I don't remember the exact error. 

So I decided to Completely remove the DB with apt-get remove mysql-Server-5.1

It gets stuck during the uninstall, I left the machine for a day and a half to uninstall mysql. 

I realized it was no use, I tried to Restart and try again, but I am getting the same thing.

```
finito@finito-desktop:~$ sudo apt-get remove mysql-server-5.1
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  dbconfig-common libhtml-template-perl mysql-server-core-5.1 libaprutil1-ldap
  apache2-mpm-prefork apache2-utils libmcrypt4 apache2.2-common libt1-5
  libaprutil1-dbd-sqlite3 apache2.2-bin wwwconfig-common php5-common
  javascript-common libjs-mootools
Use 'apt-get autoremove' to remove them.
The following packages will be REMOVED:
  mysql-server-5.1
0 upgraded, 0 newly installed, 1 to remove and 0 not upgraded.
1 not fully installed or removed.
After this operation, 15.7MB disk space will be freed.
Do you want to continue [Y/n]? y
(Reading database ... 231901 files and directories currently installed.)
Removing mysql-server-5.1 ...

```

it stays stuck at Removing mysql-server-5.1 ...

I can't progress I am at the brink now, my only option right now is format, but I don't wanna do that, can anyone please help.

This setup is almost 5 years old and I have gone with many ups and downs with it. From Windows to 8.04 to 8.10 to 9.04 to 9.10 to now 10.04 each year loving the resilience of Ubuntu and the Linux architecture. I don't want to believe that this has killed my spree.

Please help!!!:(

---

### Post by finito on 2010-07-21
Bump.

---

### Post by PeEllAvaj on 2010-07-21
If for some reason you have lost permissions on the database, the system may have trouble uninstalling it because it can't shut it down.

Have you tried killing all mysql and mysqld and mysqld_safe processes first? Make sure all of them are killed before attempting to remove it.

I also recommend apt-get purge rather than apt-get remove because purge will also delete some of your remaining configurations.

Does that help?

---

### Post by finito on 2010-07-21
still same

```
finito@finito-desktop:~$ killall mysqld
mysqld: no process found
finito@finito-desktop:~$ killall mysql
mysql: no process found
finito@finito-desktop:~$ killall mysqld_safe
mysqld_safe: no process found
finito@finito-desktop:~$ sudo dpkg --purge mysql-server
[sudo] password for finito: 
(Reading database ... 231905 files and directories currently installed.)
Removing mysql-server ...
finito@finito-desktop:~$ sudo dpkg --purge mysql-server-
mysql-server-5.1       mysql-server-core-5.1  
finito@finito-desktop:~$ sudo dpkg --purge mysql-server-5.1
(Reading database ... 231901 files and directories currently installed.)
Removing mysql-server-5.1 ...


```

---

### Post by vijayaprasadunix on 2010-07-21
hi
may i know sql developer installation

---

### Post by finito on 2010-07-21
> **vijayaprasadunix said:**
> hi
may i know sql developer installation

I am not sure what you mean? Please elaborate? or start a new thread.

---

### Post by memet on 2010-07-21
I had a similar problem.   

Try this:

Stop mysqld if it's running, and we're going to start mysqld_safe and skip that grant tables so we can get in.
```

mysqld_safe –skip-grant-tables
mysql –user=root mysql
mysql> use mysql;
mysql> UPDATE user SET Password=PASSWORD('urpassword') WHERE User='root';
mysql> drop table proc;
mysql> flush privileges;

```

Stop mysqld_safe.  That should solve your root grant problems.  But since we've tried to remove mysql let's completely remove it and reinstall it.

```

sudo dpkg --configure -a
sudo apt-get remove mysql-server mysql-server-5.1
sudo apt-get autoremove && sudo apt-get autoclean

```

If it hangs again, just kill all dpkg processes and run the three command again.

Reboot. (not really necessary but i like to)

```

sudo apt-get install mysql-server mysql-client
sudo mysql_upgrade --force -u root -purpassword

```

Hopefully, everything runs after that.

Cheers!

---

### Post by finito on 2010-07-21
Thanks Memet, your solution looked hopeful but my Install seems too screwed

```
finito@finito-desktop:~$ sudo mysqld_safe &#8211;skip-grant-tables
[sudo] password for finito: 
100722 01:11:54 mysqld_safe Logging to syslog.
100722 01:11:54 mysqld_safe Starting mysqld daemon with databases from /var/lib/mysql
100722 01:11:55 mysqld_safe mysqld from pid file /var/lib/mysql/finito-desktop.pid ended
finito@finito-desktop:~$ 

```

---

### Post by finito on 2010-07-22
bump.

Please help.

---

### Post by finito on 2010-07-23
Bumping again.

Hopefully someone knows the solution.

---

### Post by PoMeO on 2010-07-24
[http://ubuntuforums.org/showthread.php?t=1506743](http://ubuntuforums.org/showthread.php?t=1506743)
[https://bugs.launchpad.net/ubuntu/+source/dpkg/+bug/512096](https://bugs.launchpad.net/ubuntu/+source/dpkg/+bug/512096)

---

### Post by blazer9x on 2011-04-12
First thing to do was uninstall / remove the mysql-server

apt-get remove mysql-server -y
or
apt-get remove mysql-* -y

then make a simple bash script that will be used for deleting all mysql from your server / computer

cd /home/
updatedb
locate mysql > MYSQLfile
nano MYSQLremove.sh

inside MYSQLremove.sh =

#start file
#bin/bash

FILE=MYSQLfile

for aaa in $(cat $FILE)
do
echo $aaa
#for see which file has been deleted
rm -rf $aaa
#delete the file
done

#end of file

save the MYSQLremove.sh file, then

bash MYSQLremove.sh

maybe this helps :D

im doin that and i try to recompile mysql
now mysql works like a charm in my computer :D

---

