---
title: "Lost connection to MySQL server at 'reading initial communication packet', system err"
date: 2012-02-06
forum: General Help
---

### Post by semka on 2012-02-06
Hello all!

Please help me with my mysql remote connection.

I have server Ubuntu, and i need mysql with remote acces.


Error message: Lost connection to MySQL server at 'reading initial communication packet', system error: 111

mysql> show status like 'aborted%';
+------------------+-------+
| Variable_name    | Value |
+------------------+-------+
| Aborted_clients  | 0     |
| Aborted_connects | 0     |
+------------------+-------+
2 rows in set (0.00 sec)

mysql> show variables like 'connect%';
+-----------------+-------+
| Variable_name   | Value |
+-----------------+-------+
| connect_timeout | 10    |
+-----------------+-------+
1 row in set (0.00 sec)

mysql> show variables like 'version%';
+-------------------------+---------------------+
| Variable_name           | Value               |
+-------------------------+---------------------+
| version                 | 5.1.41-3ubuntu12.10 |
| version_comment         | (Ubuntu)            |
| version_compile_machine | x86_64              |
| version_compile_os      | debian-linux-gnu    |
+-------------------------+---------------------+
4 rows in set (0.00 sec)


root@580:~# dpkg -l | grep mysql
ii  libdbd-mysql-perl                4.012-1ubuntu1                         A Perl5 database interface to the MySQL data
ii  libmysql-ruby1.8                 2.8.2-1                                MySQL module for Ruby 1.8
ii  libmysqlclient16                 5.1.41-3ubuntu12.10                    MySQL database client library
ii  mysql-client-5.1                 5.1.41-3ubuntu12.10                    MySQL database client binaries
ii  mysql-client-core-5.1            5.1.41-3ubuntu12.10                    MySQL database core client binaries
ii  mysql-common                     5.1.41-3ubuntu12.10                    MySQL database common files (e.g. /etc/mysql
ii  mysql-server                     5.1.41-3ubuntu12.10                    MySQL database server (metapackage depending
ii  mysql-server-5.1                 5.1.41-3ubuntu12.10                    MySQL database server binaries
ii  mysql-server-core-5.1            5.1.41-3ubuntu12.10                    MySQL database core server files
ii  php5-mysql                       5.3.2-1ubuntu4.9                       MySQL module for php5

root@580:~# netstat -apn | grep LIST | grep 3306
tcp        0      0 ipservermysql:3306      0.0.0.0:*               LISTEN      6368/mysqld
unix  2      [ ACC ]     STREAM     LISTENING     33306    6368/mysqld         /var/run/mysqld/mysqld.sock


root@580:~# mysqld -V
mysqld  Ver 5.1.41-3ubuntu12.10 for debian-linux-gnu on x86_64 ((Ubuntu))
root@580:~# mysql -V
mysql  Ver 14.14 Distrib 5.1.41, for debian-linux-gnu (x86_64) using readline 6.1

Users with grant priveleges ok
Admin hosting panel - Plesk 10.4.4

If somebody can help me, i can paid $ via paypal.

---

### Post by semka on 2012-02-06
Please help me...

---

### Post by semka on 2012-02-06
ppfff..... :((

---

### Post by wojox on 2012-02-06
What's in your 
```
cat /etc/my.conf 
```

---

### Post by semka on 2012-02-06
> **wojox said:**
> What's in your 
```
cat /etc/my.conf 
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
# [http://dev.mysql.com/doc/mysql/en/server-system-variables.html](http://dev.mysql.com/doc/mysql/en/server-system-variables.html)

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
set-variable=local-infile=0
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
basedir	= /usr
datadir	= /var/lib/mysql
tmpdir		= /tmp

skip-external-locking
# skip-networking
#
# Instead of skip-networking the default is now to listen only on
# localhost which is more compatible and is not less secure.
bind-address		= 88.xxx.xx.xxx
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

---

### Post by semka on 2012-02-06
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
max_allowed_packet	= 60M

[mysql]
#no-auto-rehash	# faster start of mysql but no tab completition

[isamchk]
key_buffer		= 16M

#
# * IMPORTANT: Additional settings that can override those from this file!
#   The files must end with '.cnf', otherwise they'll be ignored.
#
!includedir /etc/mysql/conf.d/

---

### Post by semka on 2012-02-06
....help...

---

### Post by wojox on 2012-02-06
```
# skip-networking
#
# Instead of skip-networking the default is now to listen only on
# localhost which is more compatible and is not less secure.
bind-address = 88.xxx.xx.xxx
```

Try putting a real address in there and restart.

---

### Post by semka on 2012-02-07
> **wojox said:**
> ```
# skip-networking
#
# Instead of skip-networking the default is now to listen only on
# localhost which is more compatible and is not less secure.
bind-address = 88.xxx.xx.xxx
```

Try putting a real address in there and restart.

I know that. I have already putting real ip address... Dont work it :(((

---

### Post by Rafterman414 on 2012-02-07
Make sure that the port for MySQL is not blocked somehow. I ran into the same problem on CentOS because the default port for MySQL was blocked.

Try to telnet to port 3306 on your MySQL server.

---

### Post by semka on 2012-02-07
> **Rafterman414 said:**
> Make sure that the port for MySQL is not blocked somehow. I ran into the same problem on CentOS because the default port for MySQL was blocked.

Try to telnet to port 3306 on your MySQL server.

mysql -udbuser --host 88.xxx.xxx.xxx -P3306 -p

this is work perfecly, i can login with password... But this is work only at mysql server.

---

### Post by semka on 2012-02-07
This in log /var/log/mysql/error.log

120207 19:14:59 [Note] Plugin 'FEDERATED' is disabled.
120207 19:14:59  InnoDB: Started; log sequence number 3 1236545878
120207 19:14:59 [Note] Event Scheduler: Loaded 0 events
120207 19:14:59 [Note] /usr/sbin/mysqld: ready for connections.
Version: '5.1.41-3ubuntu12.10'  socket: '/var/run/mysqld/mysqld.sock'  port: 3306  (Ubuntu)
120207 19:16:08 [Note] /usr/sbin/mysqld: Normal shutdown

120207 19:16:08 [Note] Event Scheduler: Purging the queue. 0 events
120207 19:16:10 [Warning] /usr/sbin/mysqld: Forcing close of thread 1538  user: ''

120207 19:16:12  InnoDB: Starting shutdown...
120207 19:16:14  InnoDB: Shutdown completed; log sequence number 3 1236645348
120207 19:16:14 [Note] /usr/sbin/mysqld: Shutdown complete

120207 19:16:14 [Note] Plugin 'FEDERATED' is disabled.
120207 19:16:14  InnoDB: Started; log sequence number 3 1236645348
120207 19:16:14 [Note] Event Scheduler: Loaded 0 events
120207 19:16:14 [Note] /usr/sbin/mysqld: ready for connections.
Version: '5.1.41-3ubuntu12.10'  socket: '/var/run/mysqld/mysqld.sock'  port: 3306  (Ubuntu)

---

### Post by semka on 2012-02-08
up.....

---

### Post by semka on 2012-02-08
up2.....

---

### Post by semka on 2012-02-09
please need help....

root@580:~# telnet myipadress 3306
Trying myipadress...
Connected to myipadress.
Escape character is '^]'.
A
5.1.41-3ubuntu12.10z%Dib1m.0EL/FO=$;;UConnection closed by foreign host.
root@580:~#

---

