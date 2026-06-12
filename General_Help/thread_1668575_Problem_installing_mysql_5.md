---
title: "Problem installing mysql 5"
date: 2011-01-16
forum: General Help
---

### Post by mujer_esponja on 2011-01-16
Hello!
In my Ubuntu 10.10, following this [tutorial]("http://blog.sudobits.com/2010/10/27/how-to-install-mysql-on-ubuntu-10-10/"), I don't face step 2. I mean, while installing the packets, I don't face anything related to configuration.

Then, when I run a command, such a > mysql -u root -p, I get this error:


> ERROR 2002 (HY000): Can't connect to local MySQL server through socket '/var/run/mysqld/mysqld.sock' (2)

As I see in other treads, > ps aux | grep mysqld gives me just this output:

> 1000      4508  0.0  0.0   5172   760 pts/0    S+   19:53   0:00 grep --color=auto mysqld


What is happening??
Thanks in advance

---

### Post by mujer_esponja on 2011-01-16
I found the solution. Uninstalled mysql and installed aain using aptitude

sudo aptitude install mysql-server

---

### Post by mujer_esponja on 2011-01-16
I found the solution. Uninstalled mysql and installed aain using aptitude

sudo aptitude install mysql-server

---

### Post by mujer_esponja on 2011-01-16
I found the solution. Uninstalled mysql and installed aain using aptitude

sudo aptitude install mysql-server

---

