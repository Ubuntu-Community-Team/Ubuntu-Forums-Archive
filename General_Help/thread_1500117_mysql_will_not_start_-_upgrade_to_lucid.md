---
title: "mysql will not start - upgrade to lucid"
date: 2010-06-02
forum: General Help
---

### Post by mr_than on 2010-06-02
Hi,

I'll post more info, but I cannot get mysql to start since updating to Lucid. It seems to be utterly silent, no log entries anywhere I can see or anything.

I've tried reinstalling the ubuntu install to no avail.

Here's the /etc/mysql/my.cnf:

(default from upgrade I suspect) this is also the debian.cnf
```

# Automatically generated for Debian scripts. DO NOT TOUCH!
[client]
host     = localhost
user     = debian-sys-maint
password = jihcHi0grFmW8y2c
socket   = /var/run/mysqld/mysqld.sock
[mysql_upgrade]
host     = localhost
user     = debian-sys-maint
password = jihcHi0grFmW8y2c
socket   = /var/run/mysqld/mysqld.sock
basedir  = /usr

```



and my original one:
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
socket        = /var/run/mysqld/mysqld.sock
port        = 3306
basedir        = /usr
datadir        = /var/lib/mysql
tmpdir        = /tmp
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
thread_stack        = 192K
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
query_cache_limit    = 1M
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
max_allowed_packet    = 16M

[mysql]
#no-auto-rehash    # faster start of mysql but no tab completition

[isamchk]
key_buffer        = 16M

#
# * IMPORTANT: Additional settings that can override those from this file!
#   The files must end with '.cnf', otherwise they'll be ignored.
#

```


I'm just getting utterly nothing in any log. 

root@linuxbox:/etc/mysql# sudo start mysql
start: Job is already running: mysql

but there isn't! top/ps show nothing at all

root@linuxbox:/etc/mysql# sudo restart mysql (or stopping) just sit there, hung on something.

Any assistance with settings or some other log to look in would be wonderful!

Thanks, 

- Nathaniel

---

### Post by mattcasters on 2010-06-03
I ran into something similar.  For me the solution was to run 

sudo mysqld

Then you'll get feedback on what goes wrong with the startup.  In my case I had a typo in one of the parameters in my.cnf

Apparently the start and stop utilities are not bullet-proof to put it mildly.  You would think that if they did a big change like swapping out /etc/init.d that they would have tested it a bit.

Oh well!

Matt

---

### Post by mr_than on 2010-06-03
Thank you! That's at least got me some errors. Nothing worse than complete silence. Is there any way of enforcing extra logging with the whole service thing? I've not had much fun with it with it's introduction in 9.10.

```


100603 21:58:26 [Warning] Can't create test file /var/lib/mysql/linuxbox.lower-test
100603 21:58:26 [Warning] Can't create test file /var/lib/mysql/linuxbox.lower-test
100603 21:58:26 [Note] Plugin 'FEDERATED' is disabled.
mysqld: Can't find file: './mysql/plugin.frm' (errno: 13)
100603 21:58:26 [ERROR] Can't open the mysql.plugin table. Please run mysql_upgrade to create it.
100603 21:58:26  InnoDB: Operating system error number 13 in a file operation.
InnoDB: The error means mysqld does not have the access rights to
InnoDB: the directory.
InnoDB: File name ./ibdata1
InnoDB: File operation call: 'open'.
InnoDB: Cannot continue operation.

```

---

