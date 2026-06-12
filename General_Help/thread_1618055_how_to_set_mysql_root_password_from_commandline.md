---
title: "how to set mysql root password from commandline?"
date: 2010-11-10
forum: General Help
---

### Post by Selmi on 2010-11-10
when i use 
apt-get install mysql-server
it asks me for root password (root for database, not for os)

is it possible to set it using commandline so this windows would not appear and i could have everything in script and not have to write it all the time manually?

---

### Post by TSJason on 2010-11-10
Hi,

I think something like this should work:

```
echo mysql-server-5.1 mysql-server/root_password password PASSWORD | debconf-set-selections
echo mysql-server-5.1 mysql-server/root_password_again password PASSWORD | debconf-set-selections
apt-get install mysql-server
```

where "PASSWORD" is the password you want.

---

### Post by Selmi on 2010-11-18
it works, thanks

---

