---
title: "Mysql no longer starting"
date: 2009-08-18
forum: General Help
---

### Post by Go3Team on 2009-08-18
I just recently cloned the / drive onto a larger drive a few days ago, I don't know if this is related or not.

mysql worked perfectly before hand, and after checking my server, it doesn't appear to want to start.

Error log:
```

Aug 18 15:28:37 mythTV-MasterBackend mysqld_safe[29821]: started
Aug 18 15:28:37 mythTV-MasterBackend mysqld[29824]: 090818 15:28:37 [Warning] option 'net_buffer_length': unsigned value 8388608 adjusted to 1048576
Aug 18 15:28:37 mythTV-MasterBackend mysqld[29824]: InnoDB: Log scan progressed past the checkpoint lsn 5 2068053917
Aug 18 15:28:37 mythTV-MasterBackend mysqld[29824]: 090818 15:28:37  InnoDB: Database was not shut down normally!
Aug 18 15:28:37 mythTV-MasterBackend mysqld[29824]: InnoDB: Starting crash recovery.
Aug 18 15:28:37 mythTV-MasterBackend mysqld[29824]: InnoDB: Reading tablespace information from the .ibd files...
Aug 18 15:28:37 mythTV-MasterBackend mysqld[29824]: InnoDB: Restoring possible half-written data pages from the doublewrite
Aug 18 15:28:37 mythTV-MasterBackend mysqld[29824]: InnoDB: buffer...
Aug 18 15:28:37 mythTV-MasterBackend mysqld[29824]: InnoDB: Doing recovery: scanned up to log sequence number 5 2068066219
Aug 18 15:28:37 mythTV-MasterBackend mysqld[29824]: InnoDB: Error: trying to access page number 1761552256 in space 0,
Aug 18 15:28:37 mythTV-MasterBackend mysqld[29824]: InnoDB: space name ./ibdata1,
Aug 18 15:28:37 mythTV-MasterBackend mysqld[29824]: InnoDB: which is outside the tablespace bounds.
Aug 18 15:28:37 mythTV-MasterBackend mysqld[29824]: InnoDB: Byte offset 0, len 16384, i/o type 10.
Aug 18 15:28:37 mythTV-MasterBackend mysqld[29824]: InnoDB: If you get this error at mysqld startup, please check that
Aug 18 15:28:37 mythTV-MasterBackend mysqld[29824]: InnoDB: your my.cnf matches the ibdata files that you have in the
Aug 18 15:28:37 mythTV-MasterBackend mysqld[29824]: InnoDB: MySQL server.
Aug 18 15:28:37 mythTV-MasterBackend mysqld[29824]: 090818 15:28:37InnoDB: Assertion failure in thread 3082581696 in file fil0fil.c line 3959
Aug 18 15:28:37 mythTV-MasterBackend mysqld[29824]: InnoDB: We intentionally generate a memory trap.
Aug 18 15:28:37 mythTV-MasterBackend mysqld[29824]: InnoDB: Submit a detailed bug report to http://bugs.mysql.com.
Aug 18 15:28:37 mythTV-MasterBackend mysqld[29824]: InnoDB: If you get repeated assertion failures or crashes, even
Aug 18 15:28:37 mythTV-MasterBackend mysqld[29824]: InnoDB: immediately after the mysqld startup, there may be
Aug 18 15:28:37 mythTV-MasterBackend mysqld[29824]: InnoDB: corruption in the InnoDB tablespace. Please refer to
Aug 18 15:28:37 mythTV-MasterBackend mysqld[29824]: InnoDB: http://dev.mysql.com/doc/refman/5.0/en/forcing-recovery.html
Aug 18 15:28:37 mythTV-MasterBackend mysqld[29824]: InnoDB: about forcing recovery.
Aug 18 15:28:37 mythTV-MasterBackend mysqld[29824]: 090818 15:28:37 - mysqld got signal 11 ;
Aug 18 15:28:37 mythTV-MasterBackend mysqld[29824]: This could be because you hit a bug. It is also possible that this binary
Aug 18 15:28:37 mythTV-MasterBackend mysqld[29824]: or one of the libraries it was linked against is corrupt, improperly built,
Aug 18 15:28:37 mythTV-MasterBackend mysqld[29824]: or misconfigured. This error can also be caused by malfunctioning hardware.
Aug 18 15:28:37 mythTV-MasterBackend mysqld[29824]: We will try our best to scrape up some info that will hopefully help diagnose
Aug 18 15:28:37 mythTV-MasterBackend mysqld[29824]: the problem, but since we have already crashed, something is definitely wrong
Aug 18 15:28:37 mythTV-MasterBackend mysqld[29824]: and this may fail.
Aug 18 15:28:37 mythTV-MasterBackend mysqld[29824]: 
Aug 18 15:28:37 mythTV-MasterBackend mysqld[29824]: key_buffer_size=0
Aug 18 15:28:37 mythTV-MasterBackend mysqld[29824]: read_buffer_size=131072
Aug 18 15:28:37 mythTV-MasterBackend mysqld[29824]: max_used_connections=0
Aug 18 15:28:37 mythTV-MasterBackend mysqld[29824]: max_connections=100
Aug 18 15:28:37 mythTV-MasterBackend mysqld[29824]: threads_connected=0
Aug 18 15:28:37 mythTV-MasterBackend mysqld[29824]: It is possible that mysqld could use up to 
Aug 18 15:28:37 mythTV-MasterBackend mysqld[29824]: key_buffer_size + (read_buffer_size + sort_buffer_size)*max_connections = 733696 K
Aug 18 15:28:37 mythTV-MasterBackend mysqld[29824]: bytes of memory
Aug 18 15:28:37 mythTV-MasterBackend mysqld[29824]: Hope that's ok; if not, decrease some variables in the equation.
Aug 18 15:28:37 mythTV-MasterBackend mysqld[29824]: 
Aug 18 15:28:37 mythTV-MasterBackend mysqld[29824]: thd=(nil)
Aug 18 15:28:37 mythTV-MasterBackend mysqld[29824]: Attempting backtrace. You can use the following information to find out
Aug 18 15:28:37 mythTV-MasterBackend mysqld[29824]: where mysqld died. If you see no messages after this, something went
Aug 18 15:28:37 mythTV-MasterBackend mysqld[29824]: terribly wrong...
Aug 18 15:28:37 mythTV-MasterBackend mysqld[29824]: Cannot determine thread, fp=0xbf80c058, backtrace may not be correct.
Aug 18 15:28:37 mythTV-MasterBackend mysqld[29824]: Stack range sanity check OK, backtrace follows:
Aug 18 15:28:37 mythTV-MasterBackend mysqld[29824]: 0x81f82e6
Aug 18 15:28:37 mythTV-MasterBackend mysqld[29824]: 0x8409553
Aug 18 15:28:37 mythTV-MasterBackend mysqld[29824]: 0x83e2fa1
Aug 18 15:28:37 mythTV-MasterBackend mysqld[29824]: 0x83e3e77
Aug 18 15:28:37 mythTV-MasterBackend mysqld[29824]: 0x83d8ecd
Aug 18 15:28:37 mythTV-MasterBackend mysqld[29824]: 0x83d0b10
Aug 18 15:28:37 mythTV-MasterBackend mysqld[29824]: 0x83c34c9
Aug 18 15:28:37 mythTV-MasterBackend mysqld[29824]: 0x83c373b
Aug 18 15:28:37 mythTV-MasterBackend mysqld[29824]: 0x83c573f
Aug 18 15:28:37 mythTV-MasterBackend mysqld[29824]: 0x834501d
Aug 18 15:28:37 mythTV-MasterBackend mysqld[29824]: 0x82bf4b2
Aug 18 15:28:37 mythTV-MasterBackend mysqld[29824]: 0x82b490b
Aug 18 15:28:37 mythTV-MasterBackend mysqld[29824]: 0x81f93dd
Aug 18 15:28:37 mythTV-MasterBackend mysqld[29824]: 0x81fb6d3
Aug 18 15:28:37 mythTV-MasterBackend mysqld[29824]: Stack trace seems successful - bottom reached
Aug 18 15:28:37 mythTV-MasterBackend mysqld[29824]: Please read http://dev.mysql.com/doc/mysql/en/using-stack-trace.html and follow instructions on how to resolve the stack trace. Resolved
Aug 18 15:28:37 mythTV-MasterBackend mysqld[29824]: stack trace is much more helpful in diagnosing the problem, so please do 
Aug 18 15:28:37 mythTV-MasterBackend mysqld[29824]: resolve it
Aug 18 15:28:37 mythTV-MasterBackend mysqld[29824]: The manual page at http://dev.mysql.com/doc/mysql/en/crashing.html contains
Aug 18 15:28:37 mythTV-MasterBackend mysqld[29824]: information that should help you find out what is causing the crash.
Aug 18 15:28:37 mythTV-MasterBackend mysqld_safe[29831]: ended

```


I tried purging, and reinstalling mysql-server, which did not work.

my.cnf:
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
pid-file	= /var/run/mysqld/mysqld.pid
socket = /var/run/mysqld/mysqld.sock
port = 3306
basedir		= /usr
datadir = /var/lib/mysql
tmpdir		= /tmp
language	= /usr/share/mysql/english
skip-external-locking
#
# Instead of skip-networking the default is now to listen only on
# localhost which is more compatible and is not less secure.
bind-address = 192.168.1.100
#
# * Fine Tuning
#
key_buffer		= 16M
max_allowed_packet	= 16M
thread_stack		= 128K
thread_cache_size	= 8
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
#log		= /var/log/mysql/mysql.log
#
# Error logging goes to syslog. This is a Debian improvement :)
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
max_allowed_packet	= 16M

[mysql]
#no-auto-rehash	# faster start of mysql but no tab completition

[isamchk]
key_buffer		= 16M

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

Any help would be appreciated.

---

### Post by Go3Team on 2009-08-18
Solved - followed the directions listed here - if you use them, make sure you use the file locations for Ubuntu.

[http://www.softwareprojects.com/resources/programming/t-how-to-fix-mysql-database-myisam-innodb-1634.html](http://www.softwareprojects.com/resources/programming/t-how-to-fix-mysql-database-myisam-innodb-1634.html)

---

