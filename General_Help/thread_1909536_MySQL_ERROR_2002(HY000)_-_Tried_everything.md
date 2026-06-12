---
title: "MySQL ERROR 2002(HY000) - Tried everything"
date: 2012-01-15
forum: General Help
---

### Post by edieguez on 2012-01-15
Ever since I upgraded to Ubuntu 11.10 I cannot log into my MySQL server.  All attempts to log in result in this error:

ERROR 2002 (HY000): Can't connect to local MySQL server through socket '/var/run/mysqld/mysqld.sock' (13)

I found several threads reporting the same issue but none of the solutions posted in those threads solved the problem.  I looked inside of /var/log/mysql/error.log and found the following:

120110  2:23:06 [Note] Plugin 'FEDERATED' is disabled.
/usr/sbin/mysqld: Can't find file: './mysql/plugin.frm' (errno: 13)
120110  2:23:06 [ERROR] Can't open the mysql.plugin table. Please run mysql_upgrade to create it.
120110  2:23:06  InnoDB: Initializing buffer pool, size = 8.0M
120110  2:23:06  InnoDB: Completed initialization of buffer pool
120110  2:23:06  InnoDB: Operating system error number 13 in a file operation.
InnoDB: The error means mysqld does not have the access rights to
InnoDB: the directory.
InnoDB: File name ./ibdata1
InnoDB: File operation call: 'open'.
InnoDB: Cannot continue operation.

Trying to run “mysql_upgrade” generates its own error:

Looking for 'mysql' as: mysql
Looking for 'mysqlcheck' as: mysqlcheck
Running 'mysqlcheck' with connection arguments: '--port=3306' '--socket=/var/run/mysqld/mysqld.sock' 
mysqlcheck: Got error: 2002: Can't connect to local MySQL server through socket '/var/run/mysqld/mysqld.sock' (111) when trying to connect
FATAL ERROR: Upgrade failed


any ideas?

---

### Post by edieguez on 2012-01-15
I figured it out.  It was app armor. I had moved the data directory to /srv/mysql and that was causing a problem.  Once I updated app armor, the problem went away.

---

### Post by lisati on 2012-01-15
> **edieguez said:**
> I figured it out.  It was app armor. I had moved the data directory to /srv/mysql and that was causing a problem.  Once I updated app armor, the problem went away.

Don't forget to mark this thread as "solved".... :D

*off topic*
Speaking of app armor, I had a similar experience the other day with it interfering with correct operation of PHP on my server. After about an hour chasing my tail trying various fixes, it turned out that because I'd done a reset of my router, my server had been assigned a different IP address on my LAN. All it needed was a change to one line in one of the PHP configuration files. D'oh!

*ends*

---

