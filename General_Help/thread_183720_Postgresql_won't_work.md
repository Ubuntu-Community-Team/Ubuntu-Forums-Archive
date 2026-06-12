---
title: "Postgresql won't work"
date: 2006-05-28
forum: General Help
---

### Post by BrownieMan on 2006-05-28
Here is a copy of what I put into my terminal. I had removed and reinstalled postgresql a couple times in synaptic and now I get this error. Any ideas?

```

philip@server:~$ sudo su
Password:
root@server:/home/philip# su postgres
postgres@server:/home/philip$ createuser -d -E -P quasar-dba
Enter password for new user:
Enter it again:
Shall the new user be allowed to create more new users? (y/n) y
createuser: could not connect to database template1: could not connect to server: No such file or directory
        Is the server running locally and accepting
        connections on Unix domain socket "/var/run/postgresql/.s.PGSQL.5432"?
```

---

### Post by mindwarp on 2006-06-08
The reason you are getting this message is because postgres isn't listening on 5432.  In /etc/postgresql/8.1/main/postgresql.conf find where it says port = and make sure it says: post = 5432. If you need help after this, your problem lies in pg_hba.conf.  Just post your next error message if this is the case.

---

