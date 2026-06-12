---
title: "MySQL and databases"
date: 2012-08-11
forum: General Help
---

### Post by p3aul on 2012-08-11
Can I copy and paste a MySQL database folder created in a windows environment into the data folder in my MySQL folder in Ubuntu and get MySQL to pick it up? I know how to use root to accomplish the task.
Bar all the warnings about root , will this work?
Thanks,
Paul

---

### Post by Habitual on 2012-08-12
Better method is 
```
sudo mysqldump -u<user> -p dbname > file.sql
```then import file.sql into the new host/mysql environment.

Simply copying flat files and/or directories is asking for trouble.

---

### Post by Wim Sturkenboom on 2012-08-12
Use mysqldmp to export (sudo does not work in windows ;))
Use mysql to import in the new environment.

If the versions of mysql are the same, there is no problem copying the databases directly.

Be careful with the myseql database itself in both scenarios as ubuntu has a dedicated user in it that is used for upgrades.

> **p3aul said:**
> Bar all the warnings about root ...?
Sometimes you need to elevate privileges; so no warnings

---

