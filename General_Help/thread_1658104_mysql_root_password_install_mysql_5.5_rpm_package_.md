---
title: "mysql root password? install mysql 5.5 rpm package with alien"
date: 2011-01-02
forum: General Help
---

### Post by xirochanh on 2011-01-02
I install mysql 5.5.8 on my ubuntu 10.10 server by using rpm package, following the manual on [http://dev.mysql.com/doc/refman/5.5/en/linux-installation-rpm.html](http://dev.mysql.com/doc/refman/5.5/en/linux-installation-rpm.html). I did via alien tool for both mysql-server & mysql-client:
alien -i mysql5.5.8_package.rpm

After installing, mysql-server is running fine, I guess. But the problem is I can not log-in mysql by root account, should be empty password, the error message is: " Access denied for user 'root'@'localhost' (using password: NO)" 

So, what is the default root password? how to get or reset it? what should I do next with this installation method?

---

### Post by xirochanh on 2011-01-02
if I start mysql with --skip-grant-tables, and log-in with anonymous user, but get error:
Can't connect to local MySQL server through socket '/var/run/mysqld/mysqld.sock' (2)

by the way, how could I stop mysql server when starting with --skip-grant-tables? when I type in /etc/init.d/mysql stop, it says: MySQL server PID file could not be found!

---

### Post by P1C0 on 2011-01-02
Through the installation it must have prompted you to enter a password for root user in mysql.

I think by default mysql needs a password to access it, thus >mysql won't work, but >mysql -p will.

Try >mysql -uroot -p
and give the passworkd you entered through installation.

---

### Post by xirochanh on 2011-01-02
> **P1C0 said:**
> Through the installation it must have prompted you to enter a password for root user in mysql.

I think by default mysql needs a password to access it, thus >mysql won't work, but >mysql -p will.

Try >mysql -uroot -p
and give the passworkd you entered through installation.

Thank you, I know the reason why now. Previously, I installed mysql 5.1 with apt-get, then I just uninstall it with apt-get remove without totally remove all configuration files. So the password as same as old one.

However, I got another problem now. I decided to remove mysql 5.5, which was installed by rpm package, using alien command. I removed by apt-get purge, then reinstalled by alien again. Now, I couldn't start mysql service, it says that:

**The server quit without updating PID file (/var/lib/mysql/machinename.pid)**
I check the log.err file and see this:

  GNU nano 2.2.4              File: kubo.err

110103 10:04:49 mysqld_safe Starting mysqld daemon with databases from /var/lib$
110103 10:04:49 [Note] Plugin 'FEDERATED' is disabled.
/usr/sbin/mysqld: Table 'mysql.plugin' doesn't exist
110103 10:04:49 [ERROR] Can't open the mysql.plugin table. Please run mysql_upg$
InnoDB: The InnoDB memory heap is disabled
InnoDB: Mutexes and rw_locks use GCC atomic builtins
InnoDB: Compressed tables use zlib 1.2.3
110103 10:04:49  InnoDB: Using Linux native AIO
110103 10:04:50  InnoDB: Initializing buffer pool, size = 128.0M
110103 10:04:50  InnoDB: Completed initialization of buffer pool
110103 10:04:50  InnoDB: highest supported file format is Barracuda.
InnoDB: Log scan progressed past the checkpoint lsn 48941
110103 10:04:50  InnoDB: Database was not shut down normally!
InnoDB: Starting crash recovery.
InnoDB: Reading tablespace information from the .ibd files...
InnoDB: Restoring possible half-written data pages from the doublewrite
InnoDB: buffer...
InnoDB: Doing recovery: scanned up to log sequence number 1595675
110103 10:04:50  InnoDB: Starting an apply batch of log records to the database$
InnoDB: Progress in percents: 48 49 50 51 52 53 54 55 56 57 58 59 60 61 62 63 6$
InnoDB: Apply batch completed
110103 10:04:50  InnoDB: 1.1.4 started; log sequence number 1595675
110103 10:04:50 [ERROR] Fatal error: Can't open and lock privilege tables: Tabl$
110103 10:04:50 mysqld_safe mysqld from pid file /var/lib/mysql/machinename.pid ended



I tried again many times, still failed

---

