---
title: "MySQL Error"
date: 2009-09-19
forum: General Help
---

### Post by r_s on 2009-09-19
i was trying to install torrent in my ubunty 9.04 when it started configuring MySQL Database it shows an error

configuring MySQL database
An error seems to have occured while installing the database if it's of any help,
 this was the error encountered
ERROR 2002(HY000) can't connect to local MySQL Server through socket '/var/run/mysqld/mysqld.sock' (2)

I cannot understand what the problem is??
please help

---

### Post by scragar on 2009-09-19
Did you start the database?
```
sudo /etc/init.d/mysql start
```I cannot be 100% sure about that line, use tab-complete to help ya out.

---

### Post by r_s on 2009-09-20
yeah, I tried it but it says fails also when I try "mysql -u root -p" it gives the same error

ERROR 2002 (HY000): Can't connect to local MySQL server through socket '/var/run/mysqld/mysqld.sock' (2)

---

