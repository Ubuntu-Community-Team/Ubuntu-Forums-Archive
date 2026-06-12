---
title: "Davical database setup fails in Ubuntu 12.04"
date: 2012-08-18
forum: General Help
---

### Post by heby on 2012-08-18
Hi,

After installing Davical and Postgresql (9.1) on Ubuntu 12.04, I  tried to run the create-database script.  First, the script fails  because it cannot connect to the database (at this point it has already  created the database and the two users).  I did have the correct entries  in pg_hba.conf and had restarted postgresql.  After dropping the database users  and database again, I modified the update-davical-database script to set  the dbhost variable to 127.0.0.1 and allowed connections from localhost  to Postgres (added "host all all 127.0.0.1/32 trust" to pg_hba.conf).   Now the script gets a bit further but then breaks again with multiple  pages of error messages like the ones shown here:  

DBD::Pg::db do failed: ERROR:  permission denied for relation collection  at /usr/share/davical/dba/update-davical-database line 400,  <PERMS> line 20. 
DBD::Pg::db do failed: ERROR:  must be owner of relation collection at  /usr/share/davical/dba/update-davical-database line 410, <PERMS>  line 20. 

Has anybody seen the same issue or (even better) found a solution for it?

Thanks,
Heby

---

### Post by Azdour on 2012-08-20
Hi,

When you ran the create-database script did you run it as the postgres user?

---

### Post by heby on 2012-08-20
Hi Azdour,

Thanks for your reply.  Yes, I did run it as postgres.

---

### Post by Azdour on 2012-08-20
Hi,

I've never had any problems installing DAViCal on Ubuntu.

You may get better answers if you join the DAViCal mailing list:
 [https://lists.sourceforge.net/lists/listinfo/davical-general](https://lists.sourceforge.net/lists/listinfo/davical-general)

---

### Post by heby on 2012-08-20
Hi Azdour,

Turns out that in the end it was a strange problem with ip6tables not being fully supported on the VPS I am using.  Why that led to a "permission denied for relation" error is beyond me but it is working now...

Thanks again for your help.
Christoph

---

### Post by Azdour on 2012-08-21
Hi,

That's good to hear and be aware of.

Could you mark this thread as solved, thanks.

---

