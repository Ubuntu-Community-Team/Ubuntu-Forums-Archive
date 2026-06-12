---
title: "Mysql problem"
date: 2010-01-08
forum: General Help
---

### Post by holodila on 2010-01-08
Yesterday I installed LAMP, installed vsftpd, made both ftp and webpage work and was extremely happy :) I decided  to turn off the computer in the evening. When I turned it on again I was asked to install the fresh kernel, I installed it and rebooted. Then I found out that mysql is dead :'( My ftp is asking to log in, but the answer is wrong password or something, the webpage says "Database Error: Unable to connect to the database:Could not connect to MySQL". I logged in as root and tried ```
/etc/init.d/mysql restart
 * Stopping MySQL database server mysqld                                 [ OK ] 
 * Starting MySQL database server mysqld                                 [fail] 

```

when I try ```
mysql -u root
ERROR 2002 (HY000): Can't connect to local MySQL server through socket '/var/run/mysqld/mysqld.sock' (2)
```

my.cnf is ```
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
pid-file	= /var/run/mysqld/mysqld.pid
socket		= /var/run/mysqld/mysqld.sock
port		= 3306
basedir		= /usr
datadir		= /var/lib/mysql
tmpdir		= /tmp
skip-external-locking
#
# Instead of skip-networking the default is now to listen only on
# localhost which is more compatible and is not less secure.
bind-address		= 82.199.101.28
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
#
# Error logging goes to syslog due to /etc/mysql/conf.d/mysqld_safe_syslog.cnf.
#
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

where bindadress is my external ip. Apparently the socket is missing. I have alredy tried a lot of solutions, but none of them helped, and I don't want to do a fresh reinstall... please help :)

---

### Post by geirha on 2010-01-08
Restart it and look through /var/log/daemon.log for clues as to why it didn't start properly. You can browse the logs by going to System -> Administration -> Log viewer (or something like that), or by typing in a terminal
```
less /var/log/daemon.log
```

---

### Post by holodila on 2010-01-08
Thanks for the quick response! Restart failed, here are the logs:

```
Jan  8 19:51:27 MainPC ntpdate[4351]: adjust time server 91.189.94.4 offset 0.048980 sec
Jan  8 19:52:14 MainPC mysqld_safe: Starting mysqld daemon with databases from /var/lib/mysql
Jan  8 19:52:14 MainPC mysqld: 100108 19:52:14 [Note] Plugin 'FEDERATED' is disabled.
Jan  8 19:52:15 MainPC mysqld: 100108 19:52:15  InnoDB: Started; log sequence number 0 44233
Jan  8 19:52:15 MainPC mysqld: 100108 19:52:15 [ERROR] Can't start server: Bind on TCP/IP port: Cannot assign requested address
Jan  8 19:52:15 MainPC mysqld: 100108 19:52:15 [ERROR] Do you already have another mysqld server running on port: 3306 ?
Jan  8 19:52:15 MainPC mysqld: 100108 19:52:15 [ERROR] Aborting
Jan  8 19:52:15 MainPC mysqld: 
Jan  8 19:52:15 MainPC mysqld: 100108 19:52:15  InnoDB: Starting shutdown...
Jan  8 19:52:16 MainPC mysqld: 100108 19:52:16  InnoDB: Shutdown completed; log sequence number 0 44233
Jan  8 19:52:16 MainPC mysqld: 100108 19:52:16 [Warning] Forcing shutdown of 1 plugins
Jan  8 19:52:16 MainPC mysqld: 100108 19:52:16 [Note] /usr/sbin/mysqld: Shutdown complete
Jan  8 19:52:16 MainPC mysqld: 
Jan  8 19:52:16 MainPC mysqld_safe: mysqld from pid file /var/run/mysqld/mysqld.pid ended
Jan  8 19:52:29 MainPC /etc/init.d/mysql[4754]: 0 processes alive and '/usr/bin/mysqladmin --defaults-file=/etc/mysql/debian.cnf ping' resulted in
Jan  8 19:52:29 MainPC /etc/init.d/mysql[4754]: #007/usr/bin/mysqladmin: connect to server at 'localhost' failed
Jan  8 19:52:29 MainPC /etc/init.d/mysql[4754]: error: 'Can't connect to local MySQL server through socket '/var/run/mysqld/mysqld.sock' (2)'
Jan  8 19:52:29 MainPC /etc/init.d/mysql[4754]: Check that mysqld is running and that the socket: '/var/run/mysqld/mysqld.sock' exists!
Jan  8 19:52:29 MainPC /etc/init.d/mysql[4754]: 
(END) 

```

---

### Post by holodila on 2010-01-12
Reinstalled the system...

---

