---
title: "mysql wont start, after hard shutdown"
date: 2010-06-18
forum: General Help
---

### Post by xrado on 2010-06-18
something went wrong i had to shutdown my server manualy

now service mysql start/stop hangs ..no output

now i tried 
```
# mysqld_safe 
100618 19:59:57 mysqld_safe Logging to syslog.
100618 19:59:57 mysqld_safe Starting mysqld daemon with databases from /data/mysql
100618 19:59:57 mysqld_safe mysqld from pid file /data/mysql/xubuntu.pid ended
```

```
# tail -f /var/log/mysql/error.log  ..says

100618 19:59:57 [Note] Plugin 'FEDERATED' is disabled.
/usr/sbin/mysqld: Can't find file: './mysql/plugin.frm' (errno: 13)
100618 19:59:57 [ERROR] Can't open the mysql.plugin table. Please run mysql_upgrade to create it.
100618 19:59:57  InnoDB: Operating system error number 13 in a file operation.
InnoDB: The error means mysqld does not have the access rights to
InnoDB: the directory.
InnoDB: File name ./ibdata1
InnoDB: File operation call: 'open'.
InnoDB: Cannot continue operation.
```

Any help would be greatly appreciated

---

