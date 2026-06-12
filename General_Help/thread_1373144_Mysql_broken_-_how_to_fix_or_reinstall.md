---
title: "Mysql broken - how to fix or reinstall?"
date: 2010-01-05
forum: General Help
---

### Post by djeyewater on 2010-01-05
I found today that my mysql installation isn't working any more, I guess either a recent update has broken it or more likely MS Virtual PC suddenly closing down my VMWare Server instance that I run Ubuntu in has broken it.

Looking at the syslog, mysqld was getting blocked from applying a read mask to /sys/devices/system/cpu/, so I edited /etc/apparmor.d/usr.sbin.mysqld and added```
/sys/devices/system/cpu/ r,
```

I'm not sure if that's the correct thing to do? It got rid of the error anyway.

Next in the syslog was some InnoDB errors, so reading about this I uncommented skip innodb in /etc/mysql/my.conf. I do need InnoDB, but I thought if mysql would work without innodb, then at least I'd have an idea where the problem was.

After restarting, mysql still wouldn't start. I tried reinstalling mysql using```
sudo apt-get --purge remove mysql-server-5.1
sudo apt-get --reinstall install mysql-server-5.1
and also
sudo apt-get install mysql-server-5.1
```And also adding in the line to the apparmor file for mysql again after it had re-installed, but it still won't work.

I have also tried running```
mysqld --skip-grant
```and then```
mysql_fix_privilege_tables
mysql_upgrade
```But get the same results as [here]("http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=411672#54")

The solution given in that thread is to log into mysql and repair each table. Unless there's a quick way to do this, I don't really want to bothered with that. I don't mind all my tables etc. being lost as I just use this (Virtual) machine for developing on.

The error in syslog from the latest start looks like this:
```
Jan  5 15:56:40 rusty-ubuntu mysqld_safe: Starting mysqld daemon with databases from /var/lib/mysql
Jan  5 15:56:40 rusty-ubuntu mysqld: 100105 15:56:40 [Warning] The syntax '--log_slow_queries' is deprecated and will be removed in MySQL 7.0. Please use '--slow_query_log'/'--slow_query_log_file' instead.
Jan  5 15:56:40 rusty-ubuntu mysqld: 100105 15:56:40 [Note] Plugin 'FEDERATED' is disabled.
Jan  5 15:56:40 rusty-ubuntu mysqld: 100105 15:56:40 [Note] Plugin 'InnoDB' is disabled.
Jan  5 15:56:40 rusty-ubuntu mysqld: #007/usr/sbin/mysqld: File '/home/djeyewater/logs/mysql-slow.log' not found (Errcode: 13)
Jan  5 15:56:40 rusty-ubuntu mysqld: 100105 15:56:40 [ERROR] Could not use /home/djeyewater/logs/mysql-slow.log for logging (error 13). Turning logging off for the whole duration of the MySQL server process. To turn it on again: fix the cause, shutdown the MySQL server and restart it.
Jan  5 15:56:40 rusty-ubuntu mysqld: 100105 15:56:40 [ERROR] Fatal error: Can't open and lock privilege tables: Incorrect key file for table 'host'; try to repair it
Jan  5 15:56:40 rusty-ubuntu mysqld_safe: mysqld from pid file /var/run/mysqld/mysqld.pid ended
```

That log file it says doesn't exist DOES exist (it didn't originally, but I created it, yet it still says it doesn't exist).

The (Virtual) machine has 1GB RAM, so I don't think it should be a lack of memory causing any problems. I'm running Ubuntu 9.10 32 bit version.

Can anyone help me to get a working version of MySQL installed in Ubuntu again?

Thanks

Dave

---

### Post by bodhi.zazen on 2010-01-05
Well, I suggest you start by turning apparmor off or putting teh mysql profile into complain mode.

If it works, then the issue is with apparmor.

In that case , with teh mysql profile in complain mode, restart mysql and watch the logs in a separate terminal

```
tail -F /var/log/messages
``` and revise the apparmor profile.

If it is apparmor there are times when watching the logs does not help much :(

---

### Post by djeyewater on 2010-01-05
I tried disabling apparmor, but still get the same error when trying to start MySQL (from syslog):
```
Jan  5 19:44:47 rusty-ubuntu kernel: [13709.199966] type=1505 audit(1262720687.794:32): operation="profile_remove" pid=2936 name=/usr/sbin/mysqld namespace=default
Jan  5 19:44:47 rusty-ubuntu kernel: [13709.199969] type=1505 audit(1262720687.794:33): operation="profile_remove" pid=2936 name=/usr/sbin/tcpdump namespace=default
Jan  5 19:46:26 rusty-ubuntu mysqld_safe: Starting mysqld daemon with databases from /var/lib/mysql
Jan  5 19:46:26 rusty-ubuntu mysqld: 100105 19:46:26 [Warning] The syntax '--log_slow_queries' is deprecated and will be removed in MySQL 7.0. Please use '--slow_query_log'/'--slow_query_log_file' instead.
Jan  5 19:46:26 rusty-ubuntu mysqld: 100105 19:46:26 [Note] Plugin 'FEDERATED' is disabled.
Jan  5 19:46:26 rusty-ubuntu mysqld: 100105 19:46:26 [Note] Plugin 'InnoDB' is disabled.
Jan  5 19:46:26 rusty-ubuntu mysqld: #007/usr/sbin/mysqld: File '/home/djeyewater/logs/mysql-slow.log' not found (Errcode: 13)
Jan  5 19:46:26 rusty-ubuntu mysqld: 100105 19:46:26 [ERROR] Could not use /home/djeyewater/logs/mysql-slow.log for logging (error 13). Turning logging off for the whole duration of the MySQL server process. To turn it on again: fix the cause, shutdown the MySQL server and restart it.
Jan  5 19:46:26 rusty-ubuntu mysqld: 100105 19:46:26 [ERROR] Fatal error: Can't open and lock privilege tables: Incorrect key file for table 'host'; try to repair it
Jan  5 19:46:26 rusty-ubuntu mysqld_safe: mysqld from pid file /var/run/mysqld/mysqld.pid ended
Jan  5 19:46:41 rusty-ubuntu /etc/init.d/mysql[3259]: 0 processes alive and '/usr/bin/mysqladmin --defaults-file=/etc/mysql/debian.cnf ping' resulted in
Jan  5 19:46:41 rusty-ubuntu /etc/init.d/mysql[3259]: #007/usr/bin/mysqladmin: connect to server at 'localhost' failed
Jan  5 19:46:41 rusty-ubuntu /etc/init.d/mysql[3259]: error: 'Can't connect to local MySQL server through socket '/var/run/mysqld/mysqld.sock' (2)'
Jan  5 19:46:41 rusty-ubuntu /etc/init.d/mysql[3259]: Check that mysqld is running and that the socket: '/var/run/mysqld/mysqld.sock' exists!
Jan  5 19:46:41 rusty-ubuntu /etc/init.d/mysql[3259]: 
```

I also tried re-naming /var/lib/mysql, then running```
sudo mysql_install_db
```That ran okay, so I ran```
sudo /etc/init.d/mysql start
```But got the following output in the terminal:```
 * Starting MySQL database server mysqld                                 [ OK ] 
 * Checking for corrupt, not cleanly closed and upgrade needing tables.
djeyewater@rusty-ubuntu:~$ ERROR 1045 (28000): Access denied for user 'debian-sys-maint'@'localhost' (using password: YES)
```So I ran```
sudo dpkg-reconfigure mysql-server-5.1
```Which I thought should fix that, but got the following output in terminal:```
/usr/sbin/dpkg-reconfigure: mysql-server-5.1 is broken or not fully installed.
```

Dave

---

### Post by bodhi.zazen on 2010-01-05
The tow errors I see are 

> File '/home/djeyewater/logs/mysql-slow.log' not found 

so try ```
touch /home/djeyewater/logs/mysql-slow.log
```

The other error seems to be a password problem.

> ERROR 1045 (28000): Access denied for user 'debian-sys-maint'@'localhost' (using password: YES)

Can you connect to mysql as root ?

---

### Post by theDaveTheRave on 2010-01-05
djeyewater,

you mention that you don't mind if you "loose" all your table data?

so here is a possible test....

if you are using a "standard" my.cnf file the data directory should be set up as

> 
datadir		= /var/lib/mysql


you hence have 2 options.

create another directory an copy a "known working set of tables" into it, then point mysql to this new directory, you say the you are using the virtual machine as a "developement" environment, so why not grab a copy of the files from your "working" environment, and drop them into the filesystem somewhere, and change the datadir accordingly.

Writing this has just made me think of something else also.

Do you have enough space on your virtual machine disk for the tables?
If you don't have the space for the required tables to be read / written too then you will not be able to get the mysql daemon to start.

If you where adding in new data into the tables and you got a message error of 
> 
mysql error 1114

then this may well be your problem.

The solution is to add in a new disk, copy over the data tables to the new disk, then <mount> the new disk into the required directory.

If that is the case I can post intstructions on adding in a new HDD to a VM (if you need them), as it can be a bit 'involved'.

It took me the best part of a morning to get my VM working again when I had to figure out the process for myself.

David

---

### Post by djeyewater on 2010-01-05
> **bodhi.zazen said:**
> The tow errors I see are 



so try ```
touch /home/djeyewater/logs/mysql-slow.log
```
I've done this, and the file exists, but I'm still getting the error about it not existing (see syslog extracts below)


> **bodhi.zazen said:**
> The other error seems to be a password problem.



Can you connect to mysql as root ?
Yes, now I've re-created the MySQL data dir I can run the mysql daemon and connect to mysql as root.

> **theDaveTheRave said:**
> djeyewater,

you mention that you don't mind if you "loose" all your table data?

so here is a possible test....

if you are using a "standard" my.cnf file the data directory should be set up as



you hence have 2 options.

create another directory an copy a "known working set of tables" into it, then point mysql to this new directory, you say the you are using the virtual machine as a "developement" environment, so why not grab a copy of the files from your "working" environment, and drop them into the filesystem somewhere, and change the datadir accordingly.

While I've not done exactly this, if you see [my reply above]("http://ubuntuforums.org/showthread.php?p=8615897#3"), you can see I did something similar, and it does work up to a point. I can now run mysqld, but no user entry for the debian system maintenance user exists. Here's the relevant syslog extracts from my latest restart:
```
Jan  5 21:48:09 rusty-ubuntu kernel: [   21.002646] type=1505 audit(1262728088.587:22): operation="profile_replace" pid=858 name=/usr/sbin/mysqld
Jan  5 21:48:11 rusty-ubuntu mysqld_safe: Starting mysqld daemon with databases from /var/lib/mysql
Jan  5 21:48:11 rusty-ubuntu mysqld: 100105 21:48:11 [Warning] The syntax '--log_slow_queries' is deprecated and will be removed in MySQL 7.0. Please use '--slow_query_log'/'--slow_query_log_file' instead.
Jan  5 21:48:11 rusty-ubuntu mysqld: 100105 21:48:11 [Note] Plugin 'FEDERATED' is disabled.
Jan  5 21:48:11 rusty-ubuntu mysqld: 100105 21:48:11 [Note] Plugin 'InnoDB' is disabled.
Jan  5 21:48:11 rusty-ubuntu mysqld: #007/usr/sbin/mysqld: File '/home/djeyewater/logs/mysql-slow.log' not found (Errcode: 13)
Jan  5 21:48:11 rusty-ubuntu mysqld: 100105 21:48:11 [ERROR] Could not use /home/djeyewater/logs/mysql-slow.log for logging (error 13). Turning logging off for the whole duration of the MySQL server process. To turn it on again: fix the cause, shutdown the MySQL server and restart it.
Jan  5 21:48:11 rusty-ubuntu NetworkManager: <info>  (eth1): preparing device.
Jan  5 21:48:11 rusty-ubuntu NetworkManager: <info>  (eth1): deactivating device (reason: 2).
Jan  5 21:48:11 rusty-ubuntu mysqld: 100105 21:48:11 [Note] Event Scheduler: Loaded 0 events
Jan  5 21:48:11 rusty-ubuntu mysqld: 100105 21:48:11 [Note] /usr/sbin/mysqld: ready for connections.
Jan  5 21:48:11 rusty-ubuntu mysqld: Version: '5.1.37-1ubuntu5-log'  socket: '/var/run/mysqld/mysqld.sock'  port: 3306  (Ubuntu)
```
```
Jan  5 21:48:13 rusty-ubuntu /etc/mysql/debian-start[1218]: Upgrading MySQL tables if necessary.
Jan  5 21:48:13 rusty-ubuntu /etc/mysql/debian-start[1223]: Looking for 'mysql' as: /usr/bin/mysql
Jan  5 21:48:13 rusty-ubuntu /etc/mysql/debian-start[1223]: Looking for 'mysqlcheck' as: /usr/bin/mysqlcheck
Jan  5 21:48:13 rusty-ubuntu /etc/mysql/debian-start[1223]: Running 'mysqlcheck' with connection arguments: '--port=3306' '--socket=/var/run/mysqld/mysqld.sock' '--host=localhost' '--socket=/var/run/mysqld/mysqld.sock' '--socket=/var/run/mysqld/mysqld.sock' 
Jan  5 21:48:13 rusty-ubuntu /etc/mysql/debian-start[1223]: /usr/bin/mysqlcheck: Got error: 1045: Access denied for user 'debian-sys-maint'@'localhost' (using password: YES) when trying to connect
Jan  5 21:48:13 rusty-ubuntu /etc/mysql/debian-start[1223]: FATAL ERROR: Upgrade failed
Jan  5 21:48:13 rusty-ubuntu /etc/mysql/debian-start[1235]: Checking for insecure root accounts.
```

> **theDaveTheRave said:**
> Writing this has just made me think of something else also.

Do you have enough space on your virtual machine disk for the tables?
If you don't have the space for the required tables to be read / written too then you will not be able to get the mysql daemon to start.

If you where adding in new data into the tables and you got a message error of then this may well be your problem.

The solution is to add in a new disk, copy over the data tables to the new disk, then <mount> the new disk into the required directory.

If that is the case I can post intstructions on adding in a new HDD to a VM (if you need them), as it can be a bit 'involved'.

It took me the best part of a morning to get my VM working again when I had to figure out the process for myself.

DavidI think that free space shouldn't be the problem - if I right-click on the filesystem icon it shows 2GB free. I don't know how to add a new HDD, but I do know how to expand the current disk size, so I can increase the amount of disk space available if you think 2GB might not enough free space?

At the moment I think the main thing I need to do (please correct me if I'm wrong) is to get the debian system maintenance user added to mysql. But I don't know how to do this?

Thanks for all the help so far.

Dave

---

### Post by theDaveTheRave on 2010-01-05
djeyewater.

To add in the <debian systeme maintenence> users you could copy the mysql table from another instalation over to your system.

I'm assuming that for some reason the addition of this user isn't working when you are re-installing mysql - which seems odd.

2GB of disk space free should be enough. The question is weather you have it in the good place or not? did you partition the drive during the instalation?

the following
```

df -h

```
will show us what your partitions look like.

Personally when I created my VM I gave MySQL it's own separate partition for it's data directory. which enabled me to add in a new HDD and mount it to the desired location as and when required.

The question is did you try to add data into the tables just before you had the problem? Also if you "upgraded" this may have attempted to change data somewhere and found that it couldn't.

if you can log on to the system as the root user you can at least check to see if the <debian-sys-maint> users exists with the following query

```

select user from mysql.user

```

I don't know what the password should be for this user so I can't advise for this. However if you are able to determine what it should be you could create the user as

```

CREATE USER 'debian-sys-maint'@'localhost' identified by 'password'
[code]

from a search on the web, it seems that the password for this user is stored in the < /etc/mysql/debian.cnf > file.

So assuming that the user doesn't exist on the system you should be able to add it using the < CREATE USER... > code as above with the password from the file....

Alternatively if the account exists then the following
[code]
update user set password=PASSWORD("password from /etc/mysql/debian.cnf") where User='debian-sys-maint'

```

should solve the problem.

David.

ps. remember you may need to change the priveleges for this user

---

### Post by djeyewater on 2010-01-06
> **theDaveTheRave said:**
> 2GB of disk space free should be enough. The question is weather you have it in the good place or not? did you partition the drive during the instalation?

the following
```

df -h

```
will show us what your partitions look like.
That gives the following:
```
Filesystem            Size  Used Avail Use% Mounted on
/dev/sda1              15G   11G  3.0G  79% /
udev                  502M  224K  502M   1% /dev
none                  502M  1.2M  501M   1% /dev/shm
none                  502M  348K  501M   1% /var/run
none                  502M     0  502M   0% /var/lock
none                  502M     0  502M   0% /lib/init/rw

```

> **theDaveTheRave said:**
> I'm assuming that for some reason the addition of this user isn't working when you are re-installing mysql - which seems odd.
I tried reinstalling MySQL a few times, but that was before I'd removed and recreated the MySQL data directory. Just now my Ubuntu installed some more updates, and as part of the update process, it asked me to add a password for the mysql root user (I hadn't done this yet). After the updates had installed, I restarted my PC and it seems that the debian user is now installed:

```
mysql> select user, host from mysql.user;
+------------------+--------------+
| user             | host         |
+------------------+--------------+
| root             | 127.0.0.1    | 
| debian-sys-maint | localhost    | 
| root             | localhost    | 
| root             | rusty-ubuntu | 
+------------------+--------------+
4 rows in set (0.00 sec)
```

The relevant syslog extracts from the latest restart look like this:
```
Jan  6 10:34:21 rusty-ubuntu kernel: [   21.063400] type=1505 audit(1262774059.631:22): operation="profile_replace" pid=878 name=/usr/sbin/mysqld
Jan  6 10:34:21 rusty-ubuntu mysqld_safe: Starting mysqld daemon with databases from /var/lib/mysql
Jan  6 10:34:22 rusty-ubuntu mysqld: 100106 10:34:22 [Warning] The syntax '--log_slow_queries' is deprecated and will be removed in MySQL 7.0. Please use '--slow_query_log'/'--slow_query_log_file' instead.
Jan  6 10:34:22 rusty-ubuntu mysqld: 100106 10:34:22 [Note] Plugin 'FEDERATED' is disabled.
Jan  6 10:34:22 rusty-ubuntu mysqld: 100106 10:34:22 [Note] Plugin 'InnoDB' is disabled.
Jan  6 10:34:22 rusty-ubuntu mysqld: #007/usr/sbin/mysqld: File '/home/djeyewater/logs/mysql-slow.log' not found (Errcode: 13)
Jan  6 10:34:22 rusty-ubuntu mysqld: 100106 10:34:22 [ERROR] Could not use /home/djeyewater/logs/mysql-slow.log for logging (error 13). Turning logging off for the whole duration of the MySQL server process. To turn it on again: fix the cause, shutdown the MySQL server and restart it.
Jan  6 10:34:22 rusty-ubuntu mysqld: 100106 10:34:22 [Note] Event Scheduler: Loaded 0 events
Jan  6 10:34:22 rusty-ubuntu mysqld: 100106 10:34:22 [Note] /usr/sbin/mysqld: ready for connections.
Jan  6 10:34:22 rusty-ubuntu mysqld: Version: '5.1.37-1ubuntu5-log'  socket: '/var/run/mysqld/mysqld.sock'  port: 3306  (Ubuntu)
``````
Jan  6 10:34:24 rusty-ubuntu /etc/mysql/debian-start[1237]: Upgrading MySQL tables if necessary.
``````
Jan  6 10:34:25 rusty-ubuntu mysqld: 100106 10:34:25 [ERROR] Could not use /home/djeyewater/logs/mysql-slow.log for logging (error 13). Turning logging off for the whole duration of the MySQL server process. To turn it on again: fix the cause, shutdown the MySQL server and restart it.
Jan  6 10:34:26 rusty-ubuntu ntpdate[1308]: step time server 91.189.94.4 offset 0.504867 sec
Jan  6 10:34:27 rusty-ubuntu /etc/mysql/debian-start[1243]: Looking for 'mysql' as: /usr/bin/mysql
Jan  6 10:34:27 rusty-ubuntu /etc/mysql/debian-start[1243]: Looking for 'mysqlcheck' as: /usr/bin/mysqlcheck
Jan  6 10:34:27 rusty-ubuntu /etc/mysql/debian-start[1243]: Running 'mysqlcheck' with connection arguments: '--port=3306' '--socket=/var/run/mysqld/mysqld.sock' '--host=localhost' '--socket=/var/run/mysqld/mysqld.sock' '--socket=/var/run/mysqld/mysqld.sock' 
Jan  6 10:34:27 rusty-ubuntu /etc/mysql/debian-start[1243]: Running 'mysqlcheck' with connection arguments: '--port=3306' '--socket=/var/run/mysqld/mysqld.sock' '--host=localhost' '--socket=/var/run/mysqld/mysqld.sock' '--socket=/var/run/mysqld/mysqld.sock' 
Jan  6 10:34:27 rusty-ubuntu /etc/mysql/debian-start[1243]: mysql.columns_priv                                 OK
Jan  6 10:34:27 rusty-ubuntu /etc/mysql/debian-start[1243]: mysql.db                                           OK
Jan  6 10:34:27 rusty-ubuntu /etc/mysql/debian-start[1243]: mysql.event                                        OK
Jan  6 10:34:27 rusty-ubuntu /etc/mysql/debian-start[1243]: mysql.func                                         OK
Jan  6 10:34:27 rusty-ubuntu /etc/mysql/debian-start[1243]: mysql.general_log
Jan  6 10:34:27 rusty-ubuntu /etc/mysql/debian-start[1243]: Error    : You can't use locks with log tables.
Jan  6 10:34:27 rusty-ubuntu /etc/mysql/debian-start[1243]: status   : OK
Jan  6 10:34:27 rusty-ubuntu /etc/mysql/debian-start[1243]: mysql.help_category                                OK
Jan  6 10:34:27 rusty-ubuntu /etc/mysql/debian-start[1243]: mysql.help_keyword                                 OK
Jan  6 10:34:27 rusty-ubuntu /etc/mysql/debian-start[1243]: mysql.help_relation                                OK
Jan  6 10:34:27 rusty-ubuntu /etc/mysql/debian-start[1243]: mysql.help_topic                                   OK
Jan  6 10:34:27 rusty-ubuntu /etc/mysql/debian-start[1243]: mysql.host                                         OK
Jan  6 10:34:27 rusty-ubuntu /etc/mysql/debian-start[1243]: mysql.ndb_binlog_index                             OK
Jan  6 10:34:27 rusty-ubuntu /etc/mysql/debian-start[1243]: mysql.plugin                                       OK
Jan  6 10:34:27 rusty-ubuntu /etc/mysql/debian-start[1243]: mysql.proc                                         OK
Jan  6 10:34:27 rusty-ubuntu /etc/mysql/debian-start[1243]: mysql.procs_priv                                   OK
Jan  6 10:34:27 rusty-ubuntu /etc/mysql/debian-start[1243]: mysql.servers                                      OK
Jan  6 10:34:27 rusty-ubuntu /etc/mysql/debian-start[1243]: mysql.slow_log
Jan  6 10:34:27 rusty-ubuntu /etc/mysql/debian-start[1243]: Error    : You can't use locks with log tables.
Jan  6 10:34:27 rusty-ubuntu /etc/mysql/debian-start[1243]: status   : OK
Jan  6 10:34:27 rusty-ubuntu /etc/mysql/debian-start[1243]: mysql.tables_priv                                  OK
Jan  6 10:34:27 rusty-ubuntu /etc/mysql/debian-start[1243]: mysql.time_zone                                    OK
Jan  6 10:34:27 rusty-ubuntu /etc/mysql/debian-start[1243]: mysql.time_zone_leap_second                        OK
Jan  6 10:34:27 rusty-ubuntu /etc/mysql/debian-start[1243]: mysql.time_zone_name                               OK
Jan  6 10:34:27 rusty-ubuntu /etc/mysql/debian-start[1243]: mysql.time_zone_transition                         OK
Jan  6 10:34:27 rusty-ubuntu /etc/mysql/debian-start[1243]: mysql.time_zone_transition_type                    OK
Jan  6 10:34:27 rusty-ubuntu /etc/mysql/debian-start[1243]: mysql.user                                         OK
Jan  6 10:34:27 rusty-ubuntu /etc/mysql/debian-start[1243]: Running 'mysql_fix_privilege_tables'...
Jan  6 10:34:27 rusty-ubuntu /etc/mysql/debian-start[1243]: ERROR 29 (HY000) at line 317: File '/home/djeyewater/logs/mysql-slow.log' not found (Errcode: 13)
Jan  6 10:34:27 rusty-ubuntu /etc/mysql/debian-start[1243]: FATAL ERROR: Upgrade failed
Jan  6 10:34:27 rusty-ubuntu /etc/mysql/debian-start[1322]: Checking for insecure root accounts.
Jan  6 10:34:27 rusty-ubuntu /etc/mysql/debian-start[1326]: Triggering myisam-recover for all MyISAM tables
```

The mysql-slow.log that it says doesn't exist has the permissions rw r r, not sure if others needs to be rw for mysql to see it? I did just try adding an entry for the file with rw in the mysql apparmor config, and then restarted, but still get the same error about the file not existing in the syslog.

The syslog also has the line saying 'FATAL ERROR: Upgrade failed', but it doesn't say what the error is?

Thanks

Dave

---

### Post by theDaveTheRave on 2010-01-06
djeyewater

Your file for the mysql-slow.log

```

File '/home/djeyewater/logs/mysql-slow.log' not found

```

You mention that the log file is definately created?

I'm not 100 % sure on how access priveleges work with linux, but as a possible problem.

The file may be readable / writable by the mysql user, but if the directory it is in does not have "read write" permissions for the same user it may mean that the error lies in permissions to the whole of the path to the file, and not just the actual file.

Bodhi (as you seem to be "watching this thread"), can you confirm this situation, or point us to more info. Thanks.

The other option is
- to change the location of the mysql-slow.log file to inhabit the mysql users home directory. Also check that this is a "bonna fide" location for the log file? it may be that another option is changing the location or creating confusion (although I don't know exactly why it should).
- use a "symbolic link" to a file in the mysql users home directory to your directory so as you can more easily find it and access it when required. ~ again however I don't know precisely how file permissions will affect symbolic links - does it use the permissions of the file you are pointing to or the file that is being seen as the link?

Quickly also.

You created a single disk for your VM so there should be no problems with incorrect mount points. Also you have 3GB of space, and unless you are mad with the files you are using on your 'development' system I don't see why you should require mysql tables that inhabit more space than that.


I just had a quick google search for your error, and it threw up this bug report
[URL="http://bugs.mysql.com/bug.php?id=42028"]
http://bugs.mysql.com/bug.php?id=42028[/URL]

So if you are using mysql-5.1.39 this may explain your problem.

When you log in you will get a report of the server version you are using.

[quote]
davem@Dartagnon:~$ mysql -udavem -p
Enter password: 
Welcome to the MySQL monitor.  Commands end with ; or \g.
Your MySQL connection id is 10
Server version: 5.0.75-0ubuntu10.2 (Ubuntu)

Type 'help;' or '\h' for help. Type '\c' to clear the buffer.

mysql> 
[/code]

Hope that this explains your problems, if not you may need to add a note into the bug report

David

---

### Post by bodhi.zazen on 2010-01-06
> **theDaveTheRave said:**
> Bodhi (as you seem to be "watching this thread"), can you confirm this situation, or point us to more info. Thanks.

Good call =)

If the file exists, then yes that error message is most likely a permissions problem.

---

### Post by djeyewater on 2010-01-06
I moved the slow query log location to the mysql data location as you recommended (and also changed the syntax for controlling the log in my.cnf to ```
slow_query_log = 1
slow_query_log_file = /var/lib/mysql/mysql-slow.log
```

The mysql bug report is for a later version of mysql, I get ```
Server version: 5.1.37-1ubuntu5-log (Ubuntu)
``` when logging into mysql. 

Also, that bug just seemed to be that the person was trying to run mysql_upgrade without specifying the port properly. Looking at the debian.cnf file, the setting in there was using a socket to connect (the correct socket as specified as in my.cnf). I also checked debian-start (also in the /etc/mysql folder), and this was using the debian.cnf file when running the mysql related processes.

Anyway, since changing the location of the slow query log and restarting, I *think* mysql seems to be starting okay:
```
Jan  6 22:29:34 rusty-ubuntu kernel: [   21.933656] type=1505 audit(1262816973.483:22): operation="profile_replace" pid=896 name=/usr/sbin/mysqld
``````
Jan  6 22:29:38 rusty-ubuntu mysqld_safe: Starting mysqld daemon with databases from /var/lib/mysql
Jan  6 22:29:38 rusty-ubuntu mysqld: 100106 22:29:38 [Note] Plugin 'FEDERATED' is disabled.
Jan  6 22:29:38 rusty-ubuntu mysqld: 100106 22:29:38  InnoDB: Started; log sequence number 0 44233
``````
Jan  6 22:29:39 rusty-ubuntu mysqld: 100106 22:29:39 [Note] Event Scheduler: Loaded 0 events
Jan  6 22:29:39 rusty-ubuntu mysqld: 100106 22:29:39 [Note] /usr/sbin/mysqld: ready for connections.
Jan  6 22:29:39 rusty-ubuntu mysqld: Version: '5.1.37-1ubuntu5-log'  socket: '/var/run/mysqld/mysqld.sock'  port: 3306  (Ubuntu)
``````
Jan  6 22:29:40 rusty-ubuntu /etc/mysql/debian-start[1341]: Upgrading MySQL tables if necessary.
``````
Jan  6 22:29:42 rusty-ubuntu /etc/mysql/debian-start[1348]: Looking for 'mysql' as: /usr/bin/mysql
Jan  6 22:29:42 rusty-ubuntu /etc/mysql/debian-start[1348]: Looking for 'mysqlcheck' as: /usr/bin/mysqlcheck
Jan  6 22:29:42 rusty-ubuntu /etc/mysql/debian-start[1348]: Running 'mysqlcheck' with connection arguments: '--port=3306' '--socket=/var/run/mysqld/mysqld.sock' '--host=localhost' '--socket=/var/run/mysqld/mysqld.sock' '--socket=/var/run/mysqld/mysqld.sock' 
Jan  6 22:29:42 rusty-ubuntu /etc/mysql/debian-start[1348]: Running 'mysqlcheck' with connection arguments: '--port=3306' '--socket=/var/run/mysqld/mysqld.sock' '--host=localhost' '--socket=/var/run/mysqld/mysqld.sock' '--socket=/var/run/mysqld/mysqld.sock' 
Jan  6 22:29:42 rusty-ubuntu /etc/mysql/debian-start[1348]: mysql.columns_priv                                 OK
Jan  6 22:29:42 rusty-ubuntu /etc/mysql/debian-start[1348]: mysql.db                                           OK
Jan  6 22:29:42 rusty-ubuntu /etc/mysql/debian-start[1348]: mysql.event                                        OK
Jan  6 22:29:42 rusty-ubuntu /etc/mysql/debian-start[1348]: mysql.func                                         OK
Jan  6 22:29:42 rusty-ubuntu /etc/mysql/debian-start[1348]: mysql.general_log
Jan  6 22:29:42 rusty-ubuntu /etc/mysql/debian-start[1348]: Error    : You can't use locks with log tables.
Jan  6 22:29:42 rusty-ubuntu /etc/mysql/debian-start[1348]: status   : OK
Jan  6 22:29:42 rusty-ubuntu /etc/mysql/debian-start[1348]: mysql.help_category                                OK
Jan  6 22:29:42 rusty-ubuntu /etc/mysql/debian-start[1348]: mysql.help_keyword                                 OK
Jan  6 22:29:42 rusty-ubuntu /etc/mysql/debian-start[1348]: mysql.help_relation                                OK
Jan  6 22:29:42 rusty-ubuntu /etc/mysql/debian-start[1348]: mysql.help_topic                                   OK
Jan  6 22:29:42 rusty-ubuntu /etc/mysql/debian-start[1348]: mysql.host                                         OK
Jan  6 22:29:42 rusty-ubuntu /etc/mysql/debian-start[1348]: mysql.ndb_binlog_index                             OK
Jan  6 22:29:42 rusty-ubuntu /etc/mysql/debian-start[1348]: mysql.plugin                                       OK
Jan  6 22:29:42 rusty-ubuntu /etc/mysql/debian-start[1348]: mysql.proc                                         OK
Jan  6 22:29:42 rusty-ubuntu /etc/mysql/debian-start[1348]: mysql.procs_priv                                   OK
Jan  6 22:29:42 rusty-ubuntu /etc/mysql/debian-start[1348]: mysql.servers                                      OK
Jan  6 22:29:42 rusty-ubuntu /etc/mysql/debian-start[1348]: mysql.slow_log
Jan  6 22:29:42 rusty-ubuntu /etc/mysql/debian-start[1348]: Error    : You can't use locks with log tables.
Jan  6 22:29:42 rusty-ubuntu /etc/mysql/debian-start[1348]: status   : OK
Jan  6 22:29:42 rusty-ubuntu /etc/mysql/debian-start[1348]: mysql.tables_priv                                  OK
Jan  6 22:29:42 rusty-ubuntu /etc/mysql/debian-start[1348]: mysql.time_zone                                    OK
Jan  6 22:29:42 rusty-ubuntu /etc/mysql/debian-start[1348]: mysql.time_zone_leap_second                        OK
Jan  6 22:29:42 rusty-ubuntu /etc/mysql/debian-start[1348]: mysql.time_zone_name                               OK
Jan  6 22:29:42 rusty-ubuntu /etc/mysql/debian-start[1348]: mysql.time_zone_transition                         OK
Jan  6 22:29:42 rusty-ubuntu /etc/mysql/debian-start[1348]: mysql.time_zone_transition_type                    OK
Jan  6 22:29:42 rusty-ubuntu /etc/mysql/debian-start[1348]: mysql.user                                         OK
Jan  6 22:29:42 rusty-ubuntu /etc/mysql/debian-start[1348]: Running 'mysql_fix_privilege_tables'...
Jan  6 22:29:42 rusty-ubuntu /etc/mysql/debian-start[1348]: OK
Jan  6 22:29:42 rusty-ubuntu /etc/mysql/debian-start[1467]: Checking for insecure root accounts.
Jan  6 22:29:42 rusty-ubuntu /etc/mysql/debian-start[1472]: Triggering myisam-recover for all MyISAM tables
```

Now I just need to import the users and databases from the web server.

Thanks both of you for the help!

Dave

---

### Post by theDaveTheRave on 2010-01-06
:popcorn::popcorn::popcorn::popcorn::popcorn: :popcorn::popcorn::popcorn:

congrats on sorting that.

a quick question, did the no access to the mysql-slow.log error actually cause you problems with regards to running of the server??

I only ask because if you look at your error messages it reports that mysql is starting without logging??

```

Jan  6 10:34:22 rusty-ubuntu mysqld: #007/usr/sbin/mysqld: File '/home/djeyewater/logs/mysql-slow.log' not found (Errcode: 13)
Jan  6 10:34:22 rusty-ubuntu mysqld: 100106 10:34:22 [ERROR] Could not use /home/djeyewater/logs/mysql-slow.log for logging (error 13). Turning logging off for the whole duration of the MySQL server process. To turn it on again: fix the cause, shutdown the MySQL server and restart it.

```

so essentially it should have been OK, you just wouldn't have had any logging to the mysql-slow.log I am also aware that this isn't an "essential" of the system. I have it turned off on my laptop as I have such large data tables (5 million lines 14 columns... in case you are curious), and I would just fill up the log with every 3rd query I run! So again having this log turned off by the server shouldn't really have had any effect (or at least not as I see it).

Again, Bodhi, your wisdom would be appreciated.

Also in your original post you mentioned you "turned off innodb" from the output of the log you have turned it back on again.
I'm not sure I fully understand what you did with apparmor in your original post either (or rather how you did ??) any chance of seeing the original error, and more "idiot proof" instructions (for me) on the change in apparmor. Thanks


David

---

### Post by djeyewater on 2010-01-07
> **theDaveTheRave said:**
> a quick question, did the no access to the mysql-slow.log error actually cause you problems with regards to running of the server??

I only ask because if you look at your error messages it reports that mysql is starting without logging??
As far as I'm aware, the error with the slow log didn't affect mysql working at all.

The problem seemed to be cause by corrupt tables. Since I took many steps in trying to fix the problem, I can't be exactly sure what the cure (or problem) was, but I'm pretty sure the solution was
[LIST=1]
[*]Remove mysql data directory
[*]Re-install mysql from repository
[/LIST]

> **theDaveTheRave said:**
> Also in your original post you mentioned you "turned off innodb" from the output of the log you have turned it back on again.
Yes, I've turned InnoDB back on, and no problems so far.

> **theDaveTheRave said:**
> I'm not sure I fully understand what you did with apparmor in your original post either (or rather how you did ??) any chance of seeing the original error, and more "idiot proof" instructions (for me) on the change in apparmor.
I didn't have a copy of the error, but I've just removed the mysql rule for apparmor that I added, restarted apparmor, and then restarted mysql, and this is what I get in the syslog:
```
Jan  7 14:29:45 rusty-ubuntu kernel: [ 2251.907037] type=1503 audit(1262874585.118:35): operation="open" pid=2984 parent=2983 profile="/usr/sbin/mysqld" requested_mask="r::" denied_mask="r::" fsuid=0 ouid=0 name="/sys/devices/system/cpu/"
Jan  7 14:29:45 rusty-ubuntu mysqld: 100107 14:29:45 [Note] /usr/sbin/mysqld: Normal shutdown
Jan  7 14:29:45 rusty-ubuntu mysqld: 
Jan  7 14:29:45 rusty-ubuntu mysqld: 100107 14:29:45 [Note] Event Scheduler: Purging the queue. 0 events
Jan  7 14:29:45 rusty-ubuntu mysqld: 100107 14:29:45  InnoDB: Starting shutdown...
Jan  7 14:29:46 rusty-ubuntu mysqld: 100107 14:29:46  InnoDB: Shutdown completed; log sequence number 0 44233
Jan  7 14:29:46 rusty-ubuntu mysqld: 100107 14:29:46 [Warning] Forcing shutdown of 1 plugins
Jan  7 14:29:46 rusty-ubuntu mysqld: 100107 14:29:46 [Note] /usr/sbin/mysqld: Shutdown complete
Jan  7 14:29:46 rusty-ubuntu mysqld: 
Jan  7 14:29:46 rusty-ubuntu mysqld_safe: mysqld from pid file /var/run/mysqld/mysqld.pid ended
Jan  7 14:29:47 rusty-ubuntu kernel: [ 2254.059611] type=1503 audit(1262874587.270:36): operation="open" pid=3000 parent=2999 profile="/usr/sbin/mysqld" requested_mask="r::" denied_mask="r::" fsuid=0 ouid=0 name="/sys/devices/system/cpu/"
Jan  7 14:29:47 rusty-ubuntu kernel: [ 2254.180547] type=1503 audit(1262874587.394:37): operation="open" pid=3015 parent=3014 profile="/usr/sbin/mysqld" requested_mask="r::" denied_mask="r::" fsuid=0 ouid=0 name="/sys/devices/system/cpu/"
Jan  7 14:29:47 rusty-ubuntu kernel: [ 2254.324500] type=1503 audit(1262874587.538:38): operation="open" pid=3036 parent=3035 profile="/usr/sbin/mysqld" requested_mask="r::" denied_mask="r::" fsuid=0 ouid=0 name="/sys/devices/system/cpu/"
Jan  7 14:29:47 rusty-ubuntu mysqld_safe: Starting mysqld daemon with databases from /var/lib/mysql
Jan  7 14:29:47 rusty-ubuntu kernel: [ 2254.767478] type=1503 audit(1262874587.978:39): operation="open" pid=3165 parent=3042 profile="/usr/sbin/mysqld" requested_mask="r::" denied_mask="r::" fsuid=0 ouid=0 name="/sys/devices/system/cpu/"
Jan  7 14:29:48 rusty-ubuntu mysqld: 100107 14:29:48 [Note] Plugin 'FEDERATED' is disabled.
Jan  7 14:29:48 rusty-ubuntu mysqld: 100107 14:29:48  InnoDB: Started; log sequence number 0 44233
Jan  7 14:29:48 rusty-ubuntu mysqld: 100107 14:29:48 [Note] Event Scheduler: Loaded 0 events
Jan  7 14:29:48 rusty-ubuntu mysqld: 100107 14:29:48 [Note] /usr/sbin/mysqld: ready for connections.
Jan  7 14:29:48 rusty-ubuntu mysqld: Version: '5.1.37-1ubuntu5-log'  socket: '/var/run/mysqld/mysqld.sock'  port: 3306  (Ubuntu)
Jan  7 14:29:48 rusty-ubuntu kernel: [ 2255.459068] type=1503 audit(1262874588.670:40): operation="open" pid=3181 parent=3180 profile="/usr/sbin/mysqld" requested_mask="r::" denied_mask="r::" fsuid=0 ouid=0 name="/sys/devices/system/cpu/"
Jan  7 14:29:48 rusty-ubuntu kernel: [ 2255.581107] type=1503 audit(1262874588.794:41): operation="open" pid=3192 parent=3191 profile="/usr/sbin/mysqld" requested_mask="r::" denied_mask="r::" fsuid=0 ouid=0 name="/sys/devices/system/cpu/"
Jan  7 14:29:48 rusty-ubuntu /etc/mysql/debian-start[3205]: Upgrading MySQL tables if necessary.
Jan  7 14:29:48 rusty-ubuntu /etc/mysql/debian-start[3212]: Looking for 'mysql' as: /usr/bin/mysql
Jan  7 14:29:48 rusty-ubuntu /etc/mysql/debian-start[3212]: Looking for 'mysqlcheck' as: /usr/bin/mysqlcheck
Jan  7 14:29:48 rusty-ubuntu /etc/mysql/debian-start[3212]: This installation of MySQL is already upgraded to 5.1.37, use --force if you still need to run mysql_upgrade
Jan  7 14:29:48 rusty-ubuntu /etc/mysql/debian-start[3217]: Checking for insecure root accounts.
Jan  7 14:29:48 rusty-ubuntu /etc/mysql/debian-start[3221]: Triggering myisam-recover for all MyISAM tables
```
The apparmor errors in there are those that look like
```
Jan  7 14:29:48 rusty-ubuntu kernel: [ 2255.581107] type=1503 audit(1262874588.794:41): operation="open" pid=3192 parent=3191 profile="/usr/sbin/mysqld" requested_mask="r::" denied_mask="r::" fsuid=0 ouid=0 name="/sys/devices/system/cpu/"
```
To fix it, you just edit /etc/apparmor.d/usr.sbin.mysqld, and in there add the location and mask that apparmor is denying. The file already has quite a few rules in there, so you can just copy the syntax there. Obviously, your new rule needs to go within the curly brace block with all the other rules. So my extra rule looked like
```
 /sys/devices/system/cpu/ r,
```
As I said before, I don't know if adding that rule is wise or not, mysql seems to run okay even when apparmor is denying the mask request, but adding the rule does get rid of the error message in the syslog.

Dave

---

