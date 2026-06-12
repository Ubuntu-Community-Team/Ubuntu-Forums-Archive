---
title: "mysql cannot stop"
date: 2010-01-07
forum: General Help
---

### Post by rubo77 on 2010-01-07
i tried 
```
/etc/init.d/mysql stop
```
and it sais:```

 * Stopping MySQL database server mysqld            [fail] 
```
which is true, it doesent stop!

this is in /var/log/syslog:

root@geisterhaufen:/etc/mysql# Jan  7 12:05:43 geisterhaufen wpa_supplicant[1253]: CTRL-EVENT-SCAN-RESULTS 
Jan  7 12:05:43 geisterhaufen kernel: [ 5632.422461] type=1503 audit(1262862343.142:44): operation="open" pid=20655 parent=20654 profile="/usr/sbin/mysqld" requested_mask="r::" denied_mask="r::" fsuid=0 ouid=0 name="/sys/devices/system/cpu/"

---

### Post by theDaveTheRave on 2010-01-07
rubo77,

the only reason I can think for it to fail stopping the server is if the sever isn't running in the first place?

```

ps aux |grep mysql

```

will determine if it is or not.

Also if you are running in mysql-safe mode, it will automatically restart... but you should get confirmation that the process stops though, or some other comment.

also you will need to run the command as admin

```

sudo /etc/init.d/mysql stop

```

does this help your situation??

David

---

### Post by rubo77 on 2010-01-07
maybe...

ps aux |grep mysql
root      1365  0.0  0.0   4004   620 ?        S    15:24   0:00 /bin/sh /usr/bin/mysqld_safe
mysql     1500  0.3  0.9 264096 36824 ?        Sl   15:24   0:40 /usr/sbin/mysqld --basedir=/usr --datadir=/var/lib/mysql --user=mysql --pid-file=/var/run/mysqld/mysqld.pid --socket=/var/run/mysqld/mysqld.sock --port=3306
root      1505  0.0  0.0   3908   628 ?        S    15:24   0:00 logger -t mysqld -p daemon.error
ruben     6335  0.0  0.0   7344   888 pts/0    R+   19:04   0:00 grep --color=auto mysql

and still:
```

ruben@geisterhaufen:~$ sudo /etc/init.d/mysql stop
 * Stopping MySQL database server mysqld                       [fail] 
```

if it's running in savemode, why? and how can i stop it then?

i use ubuntu 9.10

---

### Post by viewlynn on 2010-01-08
you might try the ungraceful:

kill -9 "insert your process id here"

which for you should be:

sudo kill -9 1365

sudo kill -9 1500

---

### Post by 6cody5 on 2010-01-08
I think the easiest way to stop mysql is to end the process in the system monitor... but i'm just guessing.](*,)

---

### Post by theDaveTheRave on 2010-01-08
> **rubo77 said:**
> 
ps aux |grep mysql
root      1365  0.0  0.0   4004   620 ?        S    15:24   0:00 /bin/sh /usr/bin/mysqld_safe
mysql     1500  0.3  0.9 264096 36824 ?        Sl   15:24   0:40 /usr/sbin/mysqld --basedir=/usr --datadir=/var/lib/mysql --user=mysql --pid-file=/var/run/mysqld/mysqld.pid --socket=/var/run/mysqld/mysqld.sock --port=3306
root      1505  0.0  0.0   3908   628 ?        S    15:24   0:00 logger -t mysqld -p daemon.error
ruben     6335  0.0  0.0   7344   888 pts/0    R+   19:04   0:00 grep --color=auto mysql

Ok so it is definately running !


> 
and still:
```

ruben@geisterhaufen:~$ sudo /etc/init.d/mysql stop
 * Stopping MySQL database server mysqld                       [fail] 
```


strange that you don't get any error messages.

> 
if it's running in savemode, why? and how can i stop it then?


'safe' mode just means that if the server shuts down or fails for any reason it should try to immediately start up again.

in this instance if you used a < kill > command, as suggested by viewlynn (good idea maybe), the process will start up again straight away.

You could then have a look at the various logs to check for error messages - which you should probably do any way.

You can determine the location of the mysql log with

```

more /etc/mysql/my.cnf |grep log

```

here is my output...
> 
davem@Dartagnon:~$ more /etc/mysql/my.cnf |grep log
# Be aware that this log type is a performance killer.
#log		= /var/log/mysql/mysql.log
# Error logging goes to syslog. This is a Debian improvement :)
#log_slow_queries	= /var/log/mysql/mysql-slow.log
#log-queries-not-using-indexes
# The following can be used as easy to replay backup logs or for replication.
#log_bin			= /var/log/mysql/mysql-bin.log
expire_logs_days	= 10
max_binlog_size         = 100M
#binlog_do_db		= include_database_name
#binlog_ignore_db	= include_database_name
davem@Dartagnon:~$ 


which tells me that currently mysql loging is not running.

so you would need to edit the file (as root) to turn on the logging (uncomment the relevent line).

If you choose to use the mysql-admin console however you will need to start it as root also

```

gksudo mysql-admin

```

you will be prompted for your 'sudo' password, and then you will get the usual mysql admin console, from here you can activate loggin, and then start / stop the server.

In fact, thinking about it.....

Starting the mysql-admin gui from the command line, if you "stop" or "restart" the service from her you should get error messages reported to the console. If not start the logging, then stop the server to see what happens.

have you tried to 'restart' the server??

```

sudo /etc/init.d/mysql restart

```

Also you may need to use < mysqld > and not simply < mysql > ? although it doesn't make any difference on my system (I'm runnig 9.04 not 9.10).

David

---

### Post by rubo77 on 2010-01-08
my my.cnf looks the same like yours.

i uncommented the line 

log_bin = /var/log/mysql/mysql-bin.log

and restarted the computer.
now it logs there but only inserts and updates... no errors. all errors go to /var/log/syslog like before.

so i did this now:

root@geisterhaufen# tail -f /var/log/syslog &
...
root@geisterhaufen# /etc/init.d/mysql stop
 * Stopping MySQL database server mysqld                                                                                 [fail] 
root@geisterhaufen# Jan  8 11:55:55 geisterhaufen kernel: [ 2804.134868] type=1503 audit(1262948155.442:57): operation="open" pid=4911 parent=4910 profile="/usr/sbin/mysqld" requested_mask="r::" denied_mask="r::" fsuid=0 ouid=0 name="/sys/devices/system/cpu/"

root@geisterhaufen# /etc/init.d/mysql restart
 * Stopping MySQL database server mysqld                      [COLOR="Red"]  [fail] [/COLOR]
 * Starting MySQL database server mysqld                        [COLOR="Green"][ OK ] [/COLOR]
root@geisterhaufen# Jan  8 11:56:02 geisterhaufen kernel: [ 2810.702627] type=1503 audit(1262948162.012:58): operation="open" pid=4949 parent=4948 profile="/usr/sbin/mysqld" requested_mask="r::" denied_mask="r::" fsuid=0 ouid=0 name="/sys/devices/system/cpu/"
Jan  8 11:56:02 geisterhaufen kernel: [ 2810.765663] type=1503 audit(1262948162.072:59): operation="open" pid=5000 parent=4999 profile="/usr/sbin/mysqld" requested_mask="r::" denied_mask="r::" fsuid=0 ouid=0 name="/sys/devices/system/cpu/"
Jan  8 11:56:02 geisterhaufen kernel: [ 2810.794383] type=1503 audit(1262948162.102:60): operation="open" pid=5076 parent=5074 profile="/usr/sbin/mysqld" requested_mask="r::" denied_mask="r::" fsuid=0 ouid=0 name="/sys/devices/system/cpu/"

root@geisterhaufen# killall mysqld 
root@geisterhaufen# Jan  8 11:57:10 geisterhaufen mysqld: 100108 11:57:10 [Note] /usr/sbin/mysqld: Normal shutdown
Jan  8 11:57:10 geisterhaufen mysqld: 
Jan  8 11:57:10 geisterhaufen mysqld: 100108 11:57:10 [Note] Event Scheduler: Purging the queue. 0 events
Jan  8 11:57:10 geisterhaufen mysqld: 100108 11:57:10  InnoDB: Starting shutdown...
Jan  8 11:57:11 geisterhaufen mysqld: 100108 11:57:11  InnoDB: Shutdown completed; log sequence number 0 43655
Jan  8 11:57:11 geisterhaufen mysqld: 100108 11:57:11 [Warning] Forcing shutdown of 1 plugins
Jan  8 11:57:11 geisterhaufen mysqld: 100108 11:57:11 [Note] /usr/sbin/mysqld: Shutdown complete
Jan  8 11:57:11 geisterhaufen mysqld: 
Jan  8 11:57:11 geisterhaufen mysqld_safe: mysqld from pid file /var/run/mysqld/mysqld.pid ended

root@geisterhaufen#

[COLOR="Red"]and now it is stopped!!![/COLOR]
now a stop call while mysql is not running gives this:
root@geisterhaufen# /etc/init.d/mysql stop
 * Stopping MySQL database server mysqld                        [COLOR="Red"] [ OK ] [/COLOR]
root@geisterhaufen# Jan  8 11:57:42 geisterhaufen kernel: [ 2911.400787] type=1503 audit(1262948262.710:61): operation="open" pid=5887 parent=5886 profile="/usr/sbin/mysqld" requested_mask="r::" denied_mask="r::" fsuid=0 ouid=0 name="/sys/devices/system/cpu/"
Jan  8 11:57:42 geisterhaufen kernel: [ 2911.413780] type=1503 audit(1262948262.720:62): operation="open" pid=5896 parent=5895 profile="/usr/sbin/mysqld" requested_mask="r::" denied_mask="r::" fsuid=0 ouid=0 name="/sys/devices/system/cpu/"

root@geisterhaufen# /etc/init.d/mysql status
 * MySQL is stopped.

so it doesent restart.

but i still can't stop it with /etc/init.d/mysql stop after i restarted it, see:
/etc/init.d/mysql restart
```
 * Stopping MySQL database server mysqld                                                                                 [ OK ] 
 * Starting MySQL database server mysqld                                                                                        Jan  8 12:02:53 geisterhaufen kernel: [ 3222.052198] type=1503 audit(1262948573.360:66): operation="open" pid=8075 parent=8074 profile="/usr/sbin/mysqld" requested_mask="r::" denied_mask="r::" fsuid=0 ouid=0 name="/sys/devices/system/cpu/"
Jan  8 12:02:53 geisterhaufen kernel: [ 3222.075405] type=1503 audit(1262948573.380:67): operation="open" pid=8084 parent=8083 profile="/usr/sbin/mysqld" requested_mask="r::" denied_mask="r::" fsuid=0 ouid=0 name="/sys/devices/system/cpu/"
Jan  8 12:02:53 geisterhaufen kernel: [ 3222.105473] type=1503 audit(1262948573.410:68): operation="open" pid=8099 parent=8098 profile="/usr/sbin/mysqld" requested_mask="r::" denied_mask="r::" fsuid=0 ouid=0 name="/sys/devices/system/cpu/"
Jan  8 12:02:53 geisterhaufen kernel: [ 3222.137515] type=1503 audit(1262948573.440:69): operation="open" pid=8120 parent=8119 profile="/usr/sbin/mysqld" requested_mask="r::" denied_mask="r::" fsuid=0 ouid=0 name="/sys/devices/system/cpu/"
Jan  8 12:02:53 geisterhaufen mysqld_safe: Starting mysqld daemon with databases from /var/lib/mysql
Jan  8 12:02:53 geisterhaufen kernel: [ 3222.232603] type=1503 audit(1262948573.540:70): operation="open" pid=8237 parent=8126 profile="/usr/sbin/mysqld" requested_mask="r::" denied_mask="r::" fsuid=0 ouid=0 name="/sys/devices/system/cpu/"
Jan  8 12:02:53 geisterhaufen mysqld: 100108 12:02:53 [Note] Plugin 'FEDERATED' is disabled.
Jan  8 12:02:53 geisterhaufen mysqld: 100108 12:02:53  InnoDB: Started; log sequence number 0 43655
Jan  8 12:02:53 geisterhaufen mysqld: 100108 12:02:53 [Note] Event Scheduler: Loaded 0 events
Jan  8 12:02:53 geisterhaufen mysqld: 100108 12:02:53 [Note] /usr/sbin/mysqld: ready for connections.
Jan  8 12:02:53 geisterhaufen mysqld: Version: '5.1.37-1ubuntu5-log'  socket: '/var/run/mysqld/mysqld.sock'  port: 3306  (Ubuntu)
                                                                                                                         [ OK ]
 * Checking for corrupt, not cleanly closed and upgrade needing tables.
root@geisterhaufen# ERROR 1045 (28000): Access denied for user 'debian-sys-maint'@'localhost' (using password: YES)
Jan  8 12:02:54 geisterhaufen kernel: [ 3223.164803] type=1503 audit(1262948574.470:71): operation="open" pid=8253 parent=8252 profile="/usr/sbin/mysqld" requested_mask="r::" denied_mask="r::" fsuid=0 ouid=0 name="/sys/devices/system/cpu/"
Jan  8 12:02:54 geisterhaufen kernel: [ 3223.193550] type=1503 audit(1262948574.500:72): operation="open" pid=8264 parent=8263 profile="/usr/sbin/mysqld" requested_mask="r::" denied_mask="r::" fsuid=0 ouid=0 name="/sys/devices/system/cpu/"
Jan  8 12:02:54 geisterhaufen /etc/mysql/debian-start[8277]: Upgrading MySQL tables if necessary.
Jan  8 12:02:54 geisterhaufen /etc/mysql/debian-start[8281]: Looking for 'mysql' as: /usr/bin/mysql
Jan  8 12:02:54 geisterhaufen /etc/mysql/debian-start[8281]: Looking for 'mysqlcheck' as: /usr/bin/mysqlcheck
Jan  8 12:02:54 geisterhaufen /etc/mysql/debian-start[8281]: Running 'mysqlcheck' with connection arguments: '--port=3306' '--socket=/var/run/mysqld/mysqld.sock' '--host=localhost' '--socket=/var/run/mysqld/mysqld.sock' '--host=localhost' '--socket=/var/run/mysqld/mysqld.sock' 
Jan  8 12:02:54 geisterhaufen /etc/mysql/debian-start[8281]: /usr/bin/mysqlcheck: Got error: 1045: Access denied for user 'debian-sys-maint'@'localhost' (using password: YES) when trying to connect
Jan  8 12:02:54 geisterhaufen /etc/mysql/debian-start[8281]: FATAL ERROR: Upgrade failed
Jan  8 12:02:54 geisterhaufen /etc/mysql/debian-start[8291]: Checking for insecure root accounts.


```
and still:

root@geisterhaufen# /etc/init.d/mysql stop
 * Stopping MySQL database server mysqld                [COLOR="Red"][fail] [/COLOR]
root@geisterhaufen# Jan  8 12:04:44 geisterhaufen kernel: [ 3332.698089] type=1503 audit(1262948684.000:73): operation="open" pid=9097 parent=9096 profile="/usr/sbin/mysqld" requested_mask="r::" denied_mask="r::" fsuid=0 ouid=0 name="/sys/devices/system/cpu/"

---

### Post by alenis on 2010-01-08
I have a similar problem. I found that

mysqladmin -u root -p shutdown

stops the server.

---

### Post by theDaveTheRave on 2010-01-08
> 
* Checking for corrupt, not cleanly closed and upgrade needing tables.
root@geisterhaufen# ERROR 1045 (28000): Access denied for user 'debian-sys-maint'@'localhost' (using password: YES)
J


I wonder if this is where the problem lies?

The user in [this thread]("http://ubuntuforums.org/showthread.php?t=1373144") had a similar error in his syslog,

I gave the following advice to restore the correct password for the user

> 
if you can log on to the system as the root user you can at least check to see if the <debian-sys-maint> users exists with the following query

Code:

select user from mysql.user

I don't know what the password should be for this user so I can't advise for this. However if you are able to determine what it should be you could create the user as

[code]
CREATE USER 'debian-sys-maint'@'localhost' identified by 'password'
[code]

from a search on the web, it seems that the password for this user is stored in the < /etc/mysql/debian.cnf > file.

So assuming that the user doesn't exist on the system you should be able to add it using the < CREATE USER... > code as above with the password from the file....

Alternatively if the account exists then the following
Code:

update user set password=PASSWORD("password from /etc/mysql/debian.cnf") where User='debian-sys-maint'



It may be that the same actions will solve your shutdown problem (it should definately get rid of this particular error).

I'm now wondering if there as a specific update or similar that has caused this error in the debian-sys-maint user.

Can you confirm the version of the server you are using, when you log in via a terminal this information is echoed back at you.

Also check out that thread and see if you have any other similar issues. Bodhi.zazen suggested it may be an error within apparmor, as opposed to MySQL.

I'll drop him a pm to ask him his thoughts.

David

---

### Post by rubo77 on 2010-01-11
yes, that was it!

i looked here:```
sudo cat /etc/mysql/debian.cnf 

# Automatically generated for Debian scripts. DO NOT TOUCH!
[client]
host     = localhost
user     = debian-sys-maint
password = ****
socket   = /var/run/mysqld/mysqld.sock
[mysql_upgrade]
host     = localhost
user     = debian-sys-maint
password = ZHXU9M74UrQupW7E
socket   = /var/run/mysqld/mysqld.sock
basedir  = /usr

```
and went into phpmyadmin and changed the password there in 'privileges' i could edit the user debian-sys-maint in the section 'Change password'

now this works:```
 sudo /etc/init.d/mysql stop
 * Stopping MySQL database server mysqld                  [COLOR="Green"][ OK ] [/COLOR]
#
```

thx a lot!!!

---

### Post by RedScourge on 2010-03-22
I have found alot of forum postings suggesting to grant all permissions to this debian-sys-maint user in order to fix problems like this where the user may have imported a database backup from another linux distro, or otherwise somehow deleted this user.

Despite what they say, you do NOT need to grant all permissions, this is a bad habit to get into from a security standpoint.

All you need to grant is this (as root or whoever):

GRANT SHUTDOWN ON *.* TO 'debian-sys-maint'@'localhost';
GRANT SELECT ON `mysql`.`user` TO 'debian-sys-maint'@'localhost';

Because it needs to shutdown/startup, and does a test select from the users table as a sanity check to ensure the root user exists. This select is usually done by /usr/share/mysql/debian-start.inc.sh which is loaded by /etc/mysql/debian-start

---

### Post by rubo77 on 2010-03-22
on my machine that debian-sys-maint user has global rights SELECT, INSERT, UPDATE, DELETE, CREATE, DROP, RELOAD, SHUTDOWN, PROCESS, FILE, REFERENCES, INDEX, ALTER, SHOW DATABASES, SUPER, CREATE TEMPORARY TABLES, LOCK TABLES, REPLICATION SLAVE, REPLICATION CLIENT and EXECUTE  

i didn't do that, i guess, that's debian default installation.
is that too much rights?

---

### Post by davidshere on 2010-06-16
> **alenis said:**
> I have a similar problem. I found that

mysqladmin -u root -p shutdown

stops the server.

This worked for me.  Luckily I remembered the root pasword.

I had been trying to do an update.  The update could not stop the mysql server.  When I tried to stop it myself with "sudo /etc/init.d/mysql stop" it failed.  When I tried to restart it myself with "sudo /etc/init.d/mysql restart", I also had the "Access denied for user 'debian-sys-maint'@'localhost' (using password: YES)" error (soemthing I've never messed with).  

After I successfully stopped it, I ran the update and rebooted.  Now I can restart it with no errors.

---

