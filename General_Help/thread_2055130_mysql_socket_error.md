---
title: "mysql socket error"
date: 2012-09-08
forum: General Help
---

### Post by matimont on 2012-09-08
Hi when i try to run mysql -u root i get this:
Can't connect to local MySQL
server through socket '/var/run/mysqld/
mysqld.sock' (111)

do you know what may be? mysql is running.. i tried restarting and does the same thing..

---

### Post by sandyd on 2012-09-08
Please post output of
```
ps ax | grep mysql
```

---

### Post by matimont on 2012-09-08
Here'¿s the outpur:

23263 ?        Ssl    0:00 /usr/sbin/mysqld
23798 pts/0    S+     0:00 grep --color=auto mysql

Thanks,

---

### Post by matimont on 2012-09-08
I fixed it, I edited the my.cnf file and addded a "/" before the whole path to the socket and that made it work...

---

