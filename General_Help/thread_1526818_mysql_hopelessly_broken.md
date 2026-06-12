---
title: "mysql hopelessly broken"
date: 2010-07-08
forum: General Help
---

### Post by linuxNewb on 2010-07-08
When I type: mysql
I get: ERROR 2002 (HY000): Can't connect to local MySQL server through socket '/var/run/mysqld/mysqld.sock' (2)

When I type: sudo service mysql start
I get: Start: Job is already running: mysql
(note that NO mysql processes show up in ps, but hey if it says its running...)

When I type: sudo mysqld
I get: no errors, but again ps shows no mysql processes


I also did an apt-get purge mysql-server and removed the /var/lib/mysql dir then reinstalled, still nothing works. Please help. Thanks in advance.

---

