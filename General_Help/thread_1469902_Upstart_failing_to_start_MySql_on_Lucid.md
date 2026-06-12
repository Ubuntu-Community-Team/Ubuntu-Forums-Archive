---
title: "Upstart failing to start MySql on Lucid"
date: 2010-05-02
forum: General Help
---

### Post by thecapsaicinkid on 2010-05-02
mysqld not running on boot, I can start it manually with 

```

sudo -u mysql mysqld

```

If I attempt to start it with Upstart I get

```

dom@mythbox:~$ start mysql
start: Rejected send message, 1 matched rules; type="method_call", sender=":1.51" (uid=1000 pid=3891 comm="start) interface="com.ubuntu.Upstart0_6.Job" member="Start" error name="(unset)" requested_reply=0 destination="com.ubuntu.Upstart" (uid=0 pid=1 comm="/sbin/init"))

```

Any ideas?

Thanks

---

### Post by thecapsaicinkid on 2010-05-02
Spoke to soon, I can't even start it manually now

```
100503  0:03:11 [ERROR] Can't start server : Bind on unix socket: No such file or directory
100503  0:03:11 [ERROR] Do you already have another mysqld server running on socket: /var/run/mysqld/mysqld.sock ?
```

No other mysqld running

---

### Post by jetpeach on 2010-05-02
you might need sudo before that, try

sudo service mysql restart
or 
sudo service mysql start

although my mysql is running, it's not working right (mythtv can't find it)...but for me i think it's a problem with the databases...

---

### Post by thecapsaicinkid on 2010-05-03
Just a different error with sudo

```
start: Job failed to start
```


My MythTV is broken also, when I DID get mysql to start it would act like it was recording things fine but there'd be no physical file written *sigh*

---

### Post by thecapsaicinkid on 2010-05-05
Re-installing will get it to start manually again but the upstart script still doesn't work.

---

### Post by shrabok on 2010-05-12
I currently have the same issue, which has caused mythtv to no longer work. It was mentioned re-installing but will you lose your myth settings and recordings?
Also saw this thead, is there any relation to it?
[http://ubuntuforums.org/showthread.php?p=9177875#post9177875](http://ubuntuforums.org/showthread.php?p=9177875#post9177875)

---

### Post by thecapsaicinkid on 2010-05-18
my.cnf was missing


[https://bugs.launchpad.net/ubuntu/+source/mysql-dfsg-5.1/+bug/573318?comments=all](https://bugs.launchpad.net/ubuntu/+source/mysql-dfsg-5.1/+bug/573318?comments=all)

---

### Post by linux_buff on 2010-05-19
I encountered the same problem. Adding sudo solved my problem!

 sudo service mysql restart

---

### Post by mrsir115 on 2010-07-01
This isn't solved at all.

I am experiencing this problem at this very moment and the "solution" solved nothing.

mysql was working fine, up until a moment ago or so it seems, and now nothing is starting.  I did not install any updates either, so its odd.  I remember having the same problem last time too.

my.cnf exists in /etc/mysql and its right here
```

#
# The MySQL database server configuration file.
#
# You can copy this to one of:
# - "/etc/mysql/my.cnf" to set global options,
# - "~/.my.cnf" to set user-specific options.
# 
# One can use all long options that the program supports.
# Run program with --help to get a list of available options and with
# --print-defaults to see which it would actually understand and use.
#
# For explanations see
# http://dev.mysql.com/doc/mysql/en/server-system-variables.html

# This will be passed to all mysql clients
# It has been reported that passwords should be enclosed with ticks/quotes
# escpecially if they contain "#" chars...
# Remember to edit /etc/mysql/debian.cnf when changing the socket location.
[client]
port		= 3306
socket		= /var/run/mysqld/mysqld.sock

# Here is entries for some specific programs
# The following values assume you have at least 32M ram

# This was formally known as [safe_mysqld]. Both versions are currently parsed.
[mysqld_safe]
socket		= /var/run/mysqld/mysqld.sock
nice		= 0

[mysqld]
#
# * Basic Settings
#

#
# * IMPORTANT
#   If you make changes to these settings and your system uses apparmor, you may
#   also need to also adjust /etc/apparmor.d/usr.sbin.mysqld.
#

user		= mysql
socket		= /var/run/mysqld/mysqld.sock
port		= 3306
basedir		= /usr
datadir		= /var/lib/mysql
tmpdir		= /tmp
skip-external-locking
#
# Instead of skip-networking the default is now to listen only on
# localhost which is more compatible and is not less secure.
# bind-address		= 127.0.0.1
#
# * Fine Tuning
#
key_buffer		= 16M
max_allowed_packet	= 16M
thread_stack		= 192K
thread_cache_size       = 8
# This replaces the startup script and checks MyISAM tables if needed
# the first time they are touched
myisam-recover         = BACKUP
#max_connections        = 100
#table_cache            = 64
#thread_concurrency     = 10
#
# * Query Cache Configuration
#
query_cache_limit	= 1M
query_cache_size        = 16M
#
# * Logging and Replication
#
# Both location gets rotated by the cronjob.
# Be aware that this log type is a performance killer.
# As of 5.1 you can enable the log at runtime!
#general_log_file        = /var/log/mysql/mysql.log
#general_log             = 1

log_error                = /var/log/mysql/error.log

# Here you can see queries with especially long duration
#log_slow_queries	= /var/log/mysql/mysql-slow.log
#long_query_time = 2
#log-queries-not-using-indexes
#
# The following can be used as easy to replay backup logs or for replication.
# note: if you are setting up a replication slave, see README.Debian about
#       other settings you may need to change.
#server-id		= 1
#log_bin			= /var/log/mysql/mysql-bin.log
expire_logs_days	= 10
max_binlog_size         = 100M
#binlog_do_db		= include_database_name
#binlog_ignore_db	= include_database_name
#
# * InnoDB
#
# InnoDB is enabled by default with a 10MB datafile in /var/lib/mysql/.
# Read the manual for more InnoDB related options. There are many!
#
# * Security Features
#
# Read the manual, too, if you want chroot!
# chroot = /var/lib/mysql/
#
# For generating SSL certificates I recommend the OpenSSL GUI "tinyca".
#
# ssl-ca=/etc/mysql/cacert.pem
# ssl-cert=/etc/mysql/server-cert.pem
# ssl-key=/etc/mysql/server-key.pem



[mysqldump]
quick
quote-names
max_allowed_packet	= 16M

[mysql]
#no-auto-rehash	# faster start of mysql but no tab completition

[isamchk]
key_buffer		= 16M

#
# * IMPORTANT: Additional settings that can override those from this file!
#   The files must end with '.cnf', otherwise they'll be ignored.
#
!includedir /etc/mysql/conf.d/


```

Yet it does not start.  Trying to start it leads to this.

>sudo service mysql start
> mysql start
ERROR 2002 (HY000): Can't connect to local MySQL server through socket '/var/run/mysqld/mysqld.sock' (2)

---

### Post by HandeH on 2010-07-30
I have to manually start mysql (5.1.41-3ubuntu12.5 from lucid-proposed) by a command: 

```
sudo service mysql start
```

You can also use _[gnome-schedule]("apt://gnome-schedule")_ to execute that command on every boot.

---

### Post by HandeH on 2010-07-30
For me this issue was fixed by mysql 5.1.41-3ubuntu12.6 released in lucid-proposed a couple of hours ago.

---

### Post by Ni-el on 2010-07-30
Here, try this : [http://ubuntuforums.org/showpost.php?p=9649151&postcount=16](http://ubuntuforums.org/showpost.php?p=9649151&postcount=16)

A space missing in the code. Fixed for me when nothing else did!!

---

### Post by HoUsECAt on 2010-12-08
during the upgrade from 8.04 -> 10.4 my /etc/mysql/my.cnf got lost as well

SOLVED for me

---

### Post by LaurentEdel on 2011-02-25
Hello

After taking 6 hours of my (precious) time, finally got it : it was simply a filesize issue : I didn't have any place left on the partition containing the mysql data !

Hope this will help someone here...

---

### Post by snake_eyes on 2011-03-22
I have the same problem now, mysql faild to start on my Ubuntu 10.10

Anybody help please?

---

### Post by 2591kuldeep on 2011-08-29
open your /etc/mysql/my.cnf file  and set your bind address correctly(if it's incorrect) after doing that
type sudo /etc/init.d/mysql start :)
if still it doesn't work check whether mysql-server is installed on your machine or not
Hope this will help to others too, who are facing same problem

---

### Post by verysimple on 2011-09-07
Recently had the same problem on my Linode box and it got solved by adding hard drive space.

---

### Post by Gusgsm on 2011-11-08
```
ERROR 2002 (HY000): Can't connect to local MySQL server through socket '/var/run/mysqld/mysqld.sock' (2)[/QUOTE]

```

I had exactly the same response to "> mysql start". My disk was full. Freeing just a bit of space did the trick and now it is up and running. No need to tamper anything.

Thanks and solved :)

---

### Post by shaav on 2012-02-07
> **LaurentEdel said:**
> Hello

After taking 6 hours of my (precious) time, finally got it : it was simply a filesize issue : I didn't have any place left on the partition containing the mysql data !

Hope this will help someone here...

Dude, thank you!! That was my problem and you saved me a lot of time!

---

### Post by chovexano on 2012-08-27
I had the same issue, and it was because the hard drive was 100% full, d'oh.

---

