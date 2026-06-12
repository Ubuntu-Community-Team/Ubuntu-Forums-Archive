---
title: "PostgreSQL password"
date: 2009-09-11
forum: General Help
---

### Post by thePowerworks on 2009-09-11
I recently installed Ubuntu Server 9.04 and during the installation I remember it asking for a postgresql password. 

Today I tried to play around with postgresql, after editing "/etc/postgresql/8.3/main/pg_hba.conf" to allow local connections I encounter a password prompt.

I use the same password I did during installation and I get the following error:

psql: FATAL:  password authentication failed for user "donald"


Is there anyway for me to reset the password or completely wipe the postgresql configuration so I can restart clean?

Thanks!

---

### Post by eric3_14159 on 2009-10-08
Try using your normal login password.

---

