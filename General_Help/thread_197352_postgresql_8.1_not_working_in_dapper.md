---
title: "postgresql 8.1 not working in dapper"
date: 2006-06-15
forum: General Help
---

### Post by sotua on 2006-06-15
Installed 8.1 as usual, but when I try to start the db, I get this:

```
sotua@jambi ~ $ sudo /etc/init.d/postgresql-8.1 start
 * Starting PostgreSQL 8.1 database server  
 * Insecure directory in $ENV{PATH} while running with -T switch at /usr/bin/pg_ctlcluster line 52.

```

I know this is related to perlsec, but I thought this should work out of the box...

---

