---
title: "Mysql not started at boot (9.10 Karmic mythbuntu)"
date: 2009-11-09
forum: General Help
---

### Post by frog99green on 2009-11-09
Hi All,

A fresh 9.10/mythbuntu install; MySQL will not start at boot.  The init.d script is not being called yet I apparently have the right rc entries;

# update-rc.d mysql defaults
 Adding system startup for /etc/init.d/mysql ...
   /etc/rc0.d/K20mysql -> ../init.d/mysql
   /etc/rc1.d/K20mysql -> ../init.d/mysql
   /etc/rc6.d/K20mysql -> ../init.d/mysql
   /etc/rc2.d/S20mysql -> ../init.d/mysql
   /etc/rc3.d/S20mysql -> ../init.d/mysql
   /etc/rc4.d/S20mysql -> ../init.d/mysql
   /etc/rc5.d/S20mysql -> ../init.d/mysql

Help?

---

### Post by frog99green on 2009-11-11
Solved;

Changing "CONCURRENCY=none" in /etc/init.d/rc to "CONCURRENCY=shell" kills lots of old init scripts from starting.

---

### Post by manish.nema on 2009-11-27
I have tried with CONCURRENCY=none as well as CONCURRENCY=startpar 

Help me...

---

### Post by HereInOz on 2009-11-27
Just wondering what password you used for MySQL.  I have known MySQL to fail to start if you use unusual characters (uppercase letters and numbers) in the password.  

This may have been fixed, but a year or so ago it kept me amused for weeks until I found out what was going on.  

I was using a password like:  Pa55W0rd  and it was failing.  Changed it to something like:  password,   and it was a happy little camper.

---

