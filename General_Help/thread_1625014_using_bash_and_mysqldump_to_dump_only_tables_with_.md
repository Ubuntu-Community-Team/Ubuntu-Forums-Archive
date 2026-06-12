---
title: "using bash and mysqldump to dump only tables with prefixes"
date: 2010-11-18
forum: General Help
---

### Post by jjei on 2010-11-18
Let's say we have a file tables listing all the tables of a database.
Can I use grep and mysqldump to dump only tables with certain prefix? I tried

grep prefix_ tables | mysqldump -u root -p databasename > db.sql

but this takes all the tables..

---

### Post by DaithiF on 2010-11-18
```
mysqldump -u user -ppassword --database databasename --tables $(cat tables)

```

---

