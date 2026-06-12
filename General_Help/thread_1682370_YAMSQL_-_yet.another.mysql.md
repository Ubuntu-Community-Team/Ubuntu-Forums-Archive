---
title: "YAMSQL - yet.another.mysql"
date: 2011-02-05
forum: General Help
---

### Post by hackeress on 2011-02-05
Yes, everything is installed

```

me@machine:~$ dpkg -l mysql* | grep ii | awk '{ print $2 }'
mysql-admin
mysql-client
mysql-client-5.1
mysql-client-core-5.1
mysql-common
mysql-gui-tools-common
mysql-query-browser
mysql-server
mysql-server-5.1
mysql-server-core-5.1

```

[CODE:~$ ps -ef | grep mysql
me    16159 16135  0 16:48 pts/1    00:00:00 grep --color=auto mysql
[/CODE]

But it is not working.  

```

me@machine:~$ mysql
ERROR 2002 (HY000): Can't connect to local MySQL server through socket '/var/run/mysqld/mysqld.sock' (13)

me@machine:~$ mysql -u root -p
Enter password: 
ERROR 2002 (HY000): Can't connect to local MySQL server through socket '/var/run/mysqld/mysqld.sock' (13)

me@machine~$ sudo /etc/init.d/mysql restart
[sudo] password for me: 
Rather than invoking init scripts through /etc/init.d, use the service(8)
utility, e.g. service mysql restart
Since the script you are attempting to invoke has been converted to an
Upstart job, you may also use the restart(8) utility, e.g. restart mysql
start: Job is already running: mysql

```

Made sure file exists and has correct perms, methinks  (is empty, afaict)

```

me@machine:~$ ls -al /var/run/mysqld/
total 0
drwxrwxr-x  2 mysql root  60 2011-02-05 15:54 .
drwxr-xr-x 16 root  root 740 2011-02-05 15:17 ..
-rwxrwxr-x  1 root  root   0 2011-02-05 15:54 mysqld.sock

```

```

me@machine:~$ grep bind-address /etc/mysql/my.cnf
bind-address        = 127.0.0.1

```

Here's a copy of the my.cnf file in /etc/mysql/my.cnf

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
port        = 3306
socket        = /var/run/mysqld/mysqld.sock

# Here is entries for some specific programs
# The following values assume you have at least 32M ram

# This was formally known as [safe_mysqld]. Both versions are currently parsed.
[mysqld_safe]
socket        = /var/run/mysqld/mysqld.sock
nice        = 0

[mysqld]
#
# * Basic Settings
#

#
# * IMPORTANT
#   If you make changes to these settings and your system uses apparmor, you may
#   also need to also adjust /etc/apparmor.d/usr.sbin.mysqld.
#

user        = mysql
pid-file    = /var/run/mysqld/mysqld.pid
socket        = /var/run/mysqld/mysqld.sock
port        = 3306
basedir        = /usr
datadir        = /var/lib/mysql
tmpdir        = /tmp
language    = /usr/share/mysql/english
skip-external-locking
#
# Instead of skip-networking the default is now to listen only on
# localhost which is more compatible and is not less secure.
bind-address        = 127.0.0.1
#
# * Fine Tuning
#
key_buffer        = 16M
max_allowed_packet    = 16M
thread_stack        = 128K
thread_cache_size    = 8
#max_connections        = 100
#table_cache            = 64
#thread_concurrency     = 10
#
# * Query Cache Configuration
#
query_cache_limit       = 1M
query_cache_size        = 16M
#
# * Logging and Replication
#
# Both location gets rotated by the cronjob.
# Be aware that this log type is a performance killer.
#log        = /var/log/mysql/mysql.log
#
# Error logging goes to syslog. This is a Debian improvement :)
#
# Here you can see queries with especially long duration
#log_slow_queries    = /var/log/mysql/mysql-slow.log
#long_query_time = 2
#log-queries-not-using-indexes
#
# The following can be used as easy to replay backup logs or for replication.
# note: if you are setting up a replication slave, see README.Debian about
#       other settings you may need to change.
#server-id        = 1
#log_bin            = /var/log/mysql/mysql-bin.log
expire_logs_days    = 10
max_binlog_size         = 100M
#binlog_do_db        = include_database_name
#binlog_ignore_db    = include_database_name
#
# * BerkeleyDB
#
# Using BerkeleyDB is now discouraged as its support will cease in 5.1.12.
skip-bdb
#
# * InnoDB
#
# InnoDB is enabled by default with a 10MB datafile in /var/lib/mysql/.
# Read the manual for more InnoDB related options. There are many!
# You might want to disable InnoDB to shrink the mysqld process by circa 100MB.
#skip-innodb
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
max_allowed_packet    = 16M

[mysql]
#no-auto-rehash    # faster start of mysql but no tab completition

[isamchk]
key_buffer        = 16M

#
# * NDB Cluster
#
# See /usr/share/doc/mysql-server-*/README.Debian for more information.
#
# The following configuration is read by the NDB Data Nodes (ndbd processes)
# not from the NDB Management Nodes (ndb_mgmd processes).
#
# [MYSQL_CLUSTER]
# ndb-connectstring=127.0.0.1


#
# * IMPORTANT: Additional settings that can override those from this file!
# The files must end with '.cnf', otherwise they'll be ignored.
#
!includedir /etc/mysql/conf.d/

```

Can't figure this out.  TMI today; help think aloud about it?  Thx!

Need more command outputs?  Let me know.

---

### Post by asmoore82 on 2011-02-05
You should make sure MySQL is shutdown, then
remove that stale socket by hand and start it again:
```
sudo stop mysql
sudo rm /var/run/mysqld/mysqld.sock
sudo start mysql
```

---

