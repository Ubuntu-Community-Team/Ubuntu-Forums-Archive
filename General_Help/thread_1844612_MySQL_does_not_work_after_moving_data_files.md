---
title: "MySQL does not work after moving data files"
date: 2011-09-15
forum: General Help
---

### Post by guyfromfl on 2011-09-15
I wanted to move my MySQL data to a new directory, /media/Storage/data/MySQL so it is not effected when I mess with distro installs.

Using MySQL workbench, I changed the mysql data dir and innodb data dirs.

Now when I try to start the server I get:

```
ERROR 2002 (HY000): Can't connect to local MySQL server through socket '/var/run/mysqld/mysqld.sock' (2)

```

I even disabled apparmor and added an exception, but the msg stays the same..

I then, chmod -R 755 /media/Storage/data/MySQL/
then checked that Mysql-Server had owning permissions on that dir.

here is the end of the mysql error log
```
110915 11:41:37 [ERROR] Can't open the mysql.plugin table. Please run mysql_upgrade to create it.
110915 11:41:37  InnoDB: Initializing buffer pool, size = 8.0M
110915 11:41:37  InnoDB: Completed initialization of buffer pool
110915 11:41:37  InnoDB: Operating system error number 13 in a file operation.
InnoDB: The error means mysqld does not have the access rights to
InnoDB: the directory.
InnoDB: File name /media/Storage/data/ibdata1
InnoDB: File operation call: 'create'.
InnoDB: Cannot continue operation.
```

What am I doing wrong?

---

### Post by guyfromfl on 2011-09-15
Ok, making progress, but still not getting anywhere

I tried starting the daemon like this
```
/etc/init.d/mysqld start
```

and it came back with this new error:

```

110915 12:06:18 [Warning] Can't create test file /media/Storage/data/MySQL/BML-IT.lower-test
110915 12:06:18 [Warning] Can't create test file /media/Storage/data/MySQL/BML-IT.lower-test
```

when I checked ls -al on the new dir and its files the permissions belong to mysql.mysql

Is this correct?

---

### Post by guyfromfl on 2011-09-15
Ok, I'm a retard...

You have to make sure you spell ALL the dir names correctly..ha

oops :oops:

---

