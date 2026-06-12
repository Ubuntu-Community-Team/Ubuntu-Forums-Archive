---
title: "cannot start MySQL"
date: 2012-05-24
forum: General Help
---

### Post by said76 on 2012-05-24
Hi,

I have a problem with starting up MySQL on my Ubuntu Server 12.04 32bit. After having a successful compilation and installation of MySQL 5.1.63 from the source, I tried to start the MySQL server by the following commands

```
/usr/local/mysql/bin/mysqld_safe -user=mysql&
```

The result is 
mysqld_safe Logging to '/var/lib/mysql/comp1.example.com.err'.
mysqld_safe Starting mysqld daemon with databases from /var/lib/mysql
mysqld_safe mysqld from pid file /var/run/mysqld/mysqld.pid ended

Then, I tried to set a root password by running ```
/usr/local/mysql/bin/mysqladmin -u root password mypassword
```

I got the following error message:
/usr/local/mysql/bin/mysqladmin: connect to server at 'localhost' failed
error: 'Can't connect to local MySQL server through socket '/var/run/mysqld/mysqld.sock' (2)'
Check that mysqld is running and that the socket: '/var/run/mysqld/mysqld.sock' exists!

Checked the err file:
/usr/local/mysql/libexec/mysqld: Table 'mysql.plugin' doesn't exist
120524 17:11:58 [ERROR] Can't open the mysql.plugin table. Please run mysql_upg$
120524 17:11:58  InnoDB: Initializing buffer pool, size = 8.0M
120524 17:11:58  InnoDB: Completed initialization of buffer pool
120524 17:11:58  InnoDB: Started; log sequence number 0 44233
120524 17:11:58 [ERROR] /usr/local/mysql/libexec/mysqld: unknown variable 'lc-m$
120524 17:11:58 [ERROR] Aborting

I wonder what I missed here.

Thank you

---

### Post by roelforg on 2012-05-24
Is there a reason for not using the mysql from the repos?
 
Try running it via sudo

---

### Post by said76 on 2012-05-24
Thank you for your reply.

I could install it from the repos but I just want to make sure I can always keep up to date all the packages I have installed on my system.

I know it's hard but at least I know what kind of stuff I put it into my server.

Do you happen to know what's causing the error there.

Thank you

---

