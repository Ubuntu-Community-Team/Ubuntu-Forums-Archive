---
title: "MySQL problem on Natty. Cannot connect through socket."
date: 2011-08-04
forum: General Help
---

### Post by cgroza on 2011-08-04
Hello everyone.
I started building a website and now I want to get login/registration support.
But for that, I need a database.
I installed the mysql-server and php5-mysql  packages.

When I try to do:
```

mysql -u root -p

```I get this:
```
ERROR 2002 (HY000): Can't connect to local MySQL server through socket '/var/run/mysqld/mysqld.sock' (2)

```I have been told that this happens because mysql-server is not running.
So I try to start it:

```
mysqld start
```I get this:
```

110804 11:24:55 [Warning] Can't create test file /var/lib/mysql/cgroza-PyNerd.lower-test
110804 11:24:55 [Warning] Can't create test file /var/lib/mysql/cgroza-PyNerd.lower-test
mysqld: Can't change dir to '/var/lib/mysql/' (Errcode: 13)
110804 11:24:55 [ERROR] Aborting

110804 11:24:55 [Note] mysqld: Shutdown complete

```
Running it with sudo yields nothing but ps still shows that the server is not running.

]ps -ef | grep mysql confirms that mysqld is not running. Only mysql shows up.
```
cgroza@cgroza-PyNerd:~$ ps -ef | grep mysql
cgroza    5432  2052  0 11:26 pts/2    00:00:00 grep --color=auto mysql
```So I tried many things, some of them on this forum but no solution worked.

Thank you.

---

### Post by cgroza on 2011-08-05
Bump.

---

### Post by Wim Sturkenboom on 2011-08-05
Are your permissions set as below?

```

root@desktop-01:~# ls -ld /var/lib/mysql/
drwx------ 3 mysql mysql 4096 2011-08-05 14:32 /var/lib/mysql/

root@desktop-01:~# ls -l /var/lib/mysql/
total 20532
-rw-r--r-- 1 root  root         0 2011-08-05 14:32 debian-5.1.flag
-rw-rw---- 1 mysql mysql        5 2011-08-05 14:32 desktop-01.pid
-rw-rw---- 1 mysql mysql 10485760 2011-08-05 14:32 ibdata1
-rw-rw---- 1 mysql mysql  5242880 2011-08-05 14:32 ib_logfile0
-rw-rw---- 1 mysql mysql  5242880 2011-08-05 14:32 ib_logfile1
drwx------ 2 mysql root      4096 2011-08-05 14:32 mysql
-rw-rw---- 1 root  root         6 2011-08-05 14:32 mysql_upgrade_info
root@desktop-01:~# 

```

What I don't understand is why it's trying to create files.

---

### Post by cgroza on 2011-08-05
Hello, thanks for your help.

The output of ls is not identical to yours.
Here is the output:

```
cgroza@cgroza-PyNerd:~$ ls -ld /var/lib/mysql/
drwx------ 3 mysql mysql 4096 2011-08-03 09:36 /var/lib/mysql/

``````
cgroza@cgroza-PyNerd:~$ sudo ls -l /var/lib/mysql/
total 20484
-rw-r--r-- 1 mysql mysql        0 2011-08-03 09:36 debian-5.1.flag
-rw-rw---- 1 mysql mysql 10485760 2011-08-03 09:36 ibdata1
-rw-rw---- 1 mysql mysql  5242880 2011-08-03 09:36 ib_logfile0
-rw-rw---- 1 mysql mysql  5242880 2011-08-02 16:04 ib_logfile1
drwx------ 2 mysql mysql     4096 2011-08-03 09:36 mysql

```

---

### Post by Wim Sturkenboom on 2011-08-05
OK, I have the pid file because mysql is running, so the difference is not that big. Tried to do some research on the web (search for mysql lower-test'); the posts / blogs where it seems to be solved all refer to a permission issue (logical from the error) at another level (apparmor and selinux).

I've tried to fiddle with the apparmor configuration but could not reproduce your exact error; it however put 'sudo service mysql start' in a very long (or endless) loop where it was trying to access files in /var/lib/mysql; the process could be followed using tail -f /var/log/mysql/error.log

Below an extract (fyi)
```

110805 19:41:27 [Note] Plugin 'FEDERATED' is disabled.
/usr/sbin/mysqld: Can't find file: './mysql/plugin.frm' (errno: 13)
110805 19:41:27 [ERROR] Can't open the mysql.plugin table. Please run mysql_upgrade to create it.
110805 19:41:27  InnoDB: Operating system error number 13 in a file operation.
InnoDB: The error means mysqld does not have the access rights to
InnoDB: the directory.
InnoDB: File name ./ibdata1
InnoDB: File operation call: 'open'.
InnoDB: Cannot continue operation.
110805 19:41:57 [Note] Plugin 'FEDERATED' is disabled.
/usr/sbin/mysqld: Can't find file: './mysql/plugin.frm' (errno: 13)
110805 19:41:57 [ERROR] Can't open the mysql.plugin table. Please run mysql_upgrade to create it.
110805 19:41:57  InnoDB: Operating system error number 13 in a file operation.
InnoDB: The error means mysqld does not have the access rights to
InnoDB: the directory.
InnoDB: File name ./ibdata1
InnoDB: File operation call: 'open'.
InnoDB: Cannot continue operation.
110805 19:42:28 [Note] Plugin 'FEDERATED' is disabled.
/usr/sbin/mysqld: Can't find file: './mysql/plugin.frm' (errno: 13)
110805 19:42:28 [ERROR] Can't open the mysql.plugin table. Please run mysql_upgrade to create it.
110805 19:42:28  InnoDB: Operating system error number 13 in a file operation.
InnoDB: The error means mysqld does not have the access rights to
InnoDB: the directory.
InnoDB: File name ./ibdata1
InnoDB: File operation call: 'open'.
InnoDB: Cannot continue operation.
110805 19:42:58 [Note] Plugin 'FEDERATED' is disabled.
/usr/sbin/mysqld: Can't find file: './mysql/plugin.frm' (errno: 13)
110805 19:42:58 [ERROR] Can't open the mysql.plugin table. Please run mysql_upgrade to create it.
110805 19:42:58  InnoDB: Operating system error number 13 in a file operation.
InnoDB: The error means mysqld does not have the access rights to
InnoDB: the directory.
InnoDB: File name ./ibdata1
InnoDB: File operation call: 'open'.
InnoDB: Cannot continue operation.
110805 19:43:28 [Note] Plugin 'FEDERATED' is disabled.
/usr/sbin/mysqld: Can't find file: './mysql/plugin.frm' (errno: 13)
110805 19:43:28 [ERROR] Can't open the mysql.plugin table. Please run mysql_upgrade to create it.
110805 19:43:28  InnoDB: Operating system error number 13 in a file operation.
InnoDB: The error means mysqld does not have the access rights to
InnoDB: the directory.
InnoDB: File name ./ibdata1
InnoDB: File operation call: 'open'.
InnoDB: Cannot continue operation.
110805 19:43:58 [Note] Plugin 'FEDERATED' is disabled.
/usr/sbin/mysqld: Can't find file: './mysql/plugin.frm' (errno: 13)
110805 19:43:58 [ERROR] Can't open the mysql.plugin table. Please run mysql_upgrade to create it.
110805 19:43:58  InnoDB: Operating system error number 13 in a file operation.
InnoDB: The error means mysqld does not have the access rights to
InnoDB: the directory.
InnoDB: File name ./ibdata1
InnoDB: File operation call: 'open'.
InnoDB: Cannot continue operation.
110805 19:44:29 [Note] Plugin 'FEDERATED' is disabled.
/usr/sbin/mysqld: Can't find file: './mysql/plugin.frm' (errno: 13)
110805 19:44:29 [ERROR] Can't open the mysql.plugin table. Please run mysql_upgrade to create it.
110805 19:44:29  InnoDB: Operating system error number 13 in a file operation.
InnoDB: The error means mysqld does not have the access rights to
InnoDB: the directory.
InnoDB: File name ./ibdata1
InnoDB: File operation call: 'open'.
InnoDB: Cannot continue operation.
110805 19:44:59 [Note] Plugin 'FEDERATED' is disabled.
/usr/sbin/mysqld: Can't find file: './mysql/plugin.frm' (errno: 13)
110805 19:44:59 [ERROR] Can't open the mysql.plugin table. Please run mysql_upgrade to create it.
110805 19:44:59  InnoDB: Operating system error number 13 in a file operation.
InnoDB: The error means mysqld does not have the access rights to
InnoDB: the directory.
InnoDB: File name ./ibdata1
InnoDB: File operation call: 'open'.
InnoDB: Cannot continue operation.
110805 19:45:29 [Note] Plugin 'FEDERATED' is disabled.
/usr/sbin/mysqld: Can't find file: './mysql/plugin.frm' (errno: 13)
110805 19:45:29 [ERROR] Can't open the mysql.plugin table. Please run mysql_upgrade to create it.
110805 19:45:29  InnoDB: Operating system error number 13 in a file operation.
InnoDB: The error means mysqld does not have the access rights to
InnoDB: the directory.
InnoDB: File name ./ibdata1
InnoDB: File operation call: 'open'.
InnoDB: Cannot continue operation.
110805 19:45:59 [Note] Plugin 'FEDERATED' is disabled.
/usr/sbin/mysqld: Can't find file: './mysql/plugin.frm' (errno: 13)
110805 19:45:59 [ERROR] Can't open the mysql.plugin table. Please run mysql_upgrade to create it.
110805 19:45:59  InnoDB: Operating system error number 13 in a file operation.
InnoDB: The error means mysqld does not have the access rights to
InnoDB: the directory.
InnoDB: File name ./ibdata1
InnoDB: File operation call: 'open'.
InnoDB: Cannot continue operation.

```

Below my version of /etc/apparmor.d/usr.sbin.mysqld; maybe it helps.

```

# vim:syntax=apparmor
# Last Modified: Tue Jun 19 17:37:30 2007
#include <tunables/global>

/usr/sbin/mysqld {
  #include <abstractions/base>
  #include <abstractions/nameservice>
  #include <abstractions/user-tmp>
  #include <abstractions/mysql>
  #include <abstractions/winbind>

  capability dac_override,
  capability sys_resource,
  capability setgid,
  capability setuid,

  network tcp,

  /etc/hosts.allow r,
  /etc/hosts.deny r,

  /etc/mysql/*.pem r,
  /etc/mysql/conf.d/ r,
  /etc/mysql/conf.d/* r,
  /etc/mysql/my.cnf r,
  /usr/sbin/mysqld mr,
  /usr/share/mysql/** r,
  /var/log/mysql.log rw,
  /var/log/mysql.err rw,
[B]  /var/lib/mysql/ r,
  /var/lib/mysql/** rwk,
[/B]  /var/log/mysql/ r,
  /var/log/mysql/* rw,
  /var/run/mysqld/mysqld.pid w,
  /var/run/mysqld/mysqld.sock w,

  /sys/devices/system/cpu/ r,
}

```
In bold the two lines that I disabled.

I'm not sure if I can be of further help after this.

PS My version of Ubuntu is 10.04 (desktop).

---

### Post by cgroza on 2011-08-05
I commented out the 2 bold lines and the same thing happens. Maybe I have to reload the configuration file. I guess I will see the results on the next boot.

Thanks for your help.

---

### Post by cgroza on 2011-08-06
Had no luck with the above. Any ideas?

---

### Post by cgroza on 2011-08-07
bump

---

### Post by cgroza on 2011-08-08
bump, Anyone?

---

### Post by Wim Sturkenboom on 2011-08-27
I know it's a bit old but it's not marked as solved yet.

Just read a reply to the same problem somewhere else and somebody said that his/her problem was fixed by resetting the mysql root password.

Do a search in the mysql documentation ;) Or on the web. Starting the server with something like --skipgranttables (check for the exact syntax).

---

