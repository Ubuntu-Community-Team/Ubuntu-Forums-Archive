---
title: "Messed up MySQL"
date: 2010-11-14
forum: General Help
---

### Post by codeking on 2010-11-14
I just install Ubuntu on a new computer I got, and set up LAMP.  I started poking around in MySQL (more than I should have) and managed to break it.  I've been trying to fix it, but I can't.  I've done apt-get --purge mysql-client, but when I reinstall it it's the same thing.  How can I reinstall MySQL (and PHPmyadmin) from a completely clean slate?  (There's no important data on there)

---

### Post by Cuppa-Chino on 2010-11-16
Similar to where codeking is:

I installed mythtv backend yesterday and all appeared to be fine, although it took me forever to log into the mysql server, finally reset passwords, rebuilt the database from hand etc and got in

now I cannot get back in for the life of me (I have googled and googled this but no luck what-so-ever)

I just cannot seem to get the mysql server to run:

as su:
```
# mysql
ERROR 2002 (HY000): Can't connect to local MySQL server through socket '/var/run/mysqld/mysqld.sock' (2)
root@#

```

but at the same time:
```
sudo service mysql start
start: Job is already running: mysql
```

and also:
```
$ sudo dpkg-reconfigure mysql-server-5.1 
mysql stop/waiting
101117  0:04:28 [Note] Plugin 'FEDERATED' is disabled.
101117  0:04:28  InnoDB: Started; log sequence number 0 70260
101117  0:04:28  InnoDB: Starting shutdown...
101117  0:04:34  InnoDB: Shutdown completed; log sequence number 0 70260
mysql start/running
:~$ mysql
ERROR 2002 (HY000): Can't connect to local MySQL server through socket '/var/run/mysqld/mysqld.sock' (2)

```

I am totally confused, if someone could tell me a sure way to get rid of all the conflicting bits I am game, as I have nearly given up hope...

---

