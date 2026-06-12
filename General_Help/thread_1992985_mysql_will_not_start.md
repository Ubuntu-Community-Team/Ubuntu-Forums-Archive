---
title: "mysql will not start"
date: 2012-06-01
forum: General Help
---

### Post by teropita on 2012-06-01
The problem seems to have occurred either after upgrade to 11.10 or when I installed Logitech Media Server from a deb.

Error log is:

sudo mysqld gives the following in the error log
120601 22:43:57 [Note] Plugin 'FEDERATED' is disabled.
120601 22:43:57  InnoDB: Initializing buffer pool, size = 8.0M
120601 22:43:57  InnoDB: Completed initialization of buffer pool
120601 22:43:57  InnoDB: Started; log sequence number 0 279056
120601 22:43:57 [ERROR] Can't start server : Bind on unix socket: Permission denied
120601 22:43:57 [ERROR] Do you already have another mysqld server running on socket: /var/run/mysqld/mysqld.sock ?
120601 22:43:57 [ERROR] Aborting

120601 22:43:57  InnoDB: Starting shutdown...
120601 22:44:02  InnoDB: Shutdown completed; log sequence number 0 279056
120601 22:44:02 [Note] mysqld: Shutdown complete

 I don't think I have another mysqld running at least not according to ps -aef |grep mysql

/var/run/mysqld/mysqld.sock does not exist /var/run/mysqld/ is empty

I did find []("https://lists.ubuntu.com/archives/ubuntu-server-bugs/2011-October/064838.html")
and I changed 

/var/run/mysqld/mysqld.pid w,
/var/run/mysqld/mysqld.sock w,
to
/{,var/}run/mysqld/mysqld.pid w, 
 /{,var/}run/mysqld/mysqld.sock w, 

but that did not change anything - still get the permissions error

I have completely removed and reinstalled mysql many times but no change.

I would appreciate any help.

I would appreciate

---

### Post by vandorjw on 2012-06-01
```
 
ls -l /var/run/ | grep mysql

```

should return something simular to 
> 
drwxr-xr-x  2 mysql     mysql     60 Jun  1 05:46 mysqld


other than this, there isn't much additional error info you gave.
Since you said you already reinstalled a bunch of times, you can also try 

```

sudo apt-get purge mysql-sever

```

I believe this takes with it all your configuration files associated with mysql. (if you misconfigured something, and you only re-install then the bad config file will remain and problem will persist)

---

### Post by teropita on 2012-06-01
ls -l /var/run/ | grep mysql

does not return anything, which I guess is because mysql is not running

I did sudo apt-get purge mysql-server
and sudo apt-get purge mysql-client
and sudo apt-get purge mysql-common

and I also deleted /etc/apparmor.d/usr.sbin.mysqld

before reinstalling.

it now seems that mysql is running, but I am still having trouble with restoring my mythtv database, if it works out I will come back and mark this solved.

---

