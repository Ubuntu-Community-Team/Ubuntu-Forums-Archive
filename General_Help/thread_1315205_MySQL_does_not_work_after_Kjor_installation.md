---
title: "MySQL does not work after Kjor installation"
date: 2009-11-05
forum: General Help
---

### Post by OOzypal on 2009-11-05
Hello

I am getting the following error when I run mySQL. Those symptoms started after installing Kjots (KDE application) on my desktop.

In my Laptop, Kjots was already installed. After I upgraded to 9.10, the same error appeared.


```
ERROR 2002 (HY000): Can't connect to local MySQL server through socket '/var/run/mysqld/mysqld.sock' (2)
```

Thank you

---

### Post by geo.cohn on 2009-11-05
After upgrading to 9.10, LAMP applications on my 3 systems stopped working.  I found that mysqld was no longer running.

I was able to fix it by using Synaptic Package Manager to install the mysql-server package.  Evidently, in going from mysql 5.0 to 5.1, something fell through the cracks in the upgrade.

---

