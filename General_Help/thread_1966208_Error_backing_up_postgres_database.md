---
title: "Error backing up postgres database"
date: 2012-04-26
forum: General Help
---

### Post by mcraul on 2012-04-26
Im using webmin on an Ubuntu box running 10.04.1 and I wanted to setup a schedule to backup my databases. When I did a manual run through webmail it got this error

```
Failed to backup database : pg_dump failed :
pg_dump: [archiver] could not open output file "/var/backups/nearby.sql": Permission denied
Failed to backup database : pg_dump failed :
pg_dump: [archiver] could not open output file "/var/backups/nearby_demo.sql": Permission denied
Failed to backup database : pg_dump failed :
pg_dump: [archiver] could not open output file "/var/backups/nearby_test.sql": Permission denied
Failed to backup database : pg_dump failed :
pg_dump: [archiver] could not open output file "/var/backups/postgres.sql": Permission denied
Database template0 is not accepting connections.
Failed to backup database : pg_dump failed :
pg_dump: [archiver] could not open output file "/var/backups/template1.sql": Permission denied
Scheduled backup for database left disabled.
```

Now how do I make sure the user  running the backup script has permission to run it?

Thanks!

---

### Post by mcraul on 2012-04-26
From what I understand the postgres user has to be a super user to run backups? is that right? how do i find out?

Thanks!

---

### Post by QIII on 2012-04-26
Only superusers can add/modify stuff in directories like /var unless a superuser specifically changes the permissions.

That's why you are getting the permission denied message.

You need to dump the file to some place the user has permissions.

---

### Post by mcraul on 2012-04-26
Thanks for the reply.

So right now i'm trying to dump the back up here

/var/backups

and it has permissions correctly I think


drwxr-xr-x  3 root root  4096 Apr 26 15:35 backups


What user does webmin use to run the backup? is it the root?
If it is then root should have permission to write to that directory no?

or am i getting this all wrong?

Thanks again!

---

