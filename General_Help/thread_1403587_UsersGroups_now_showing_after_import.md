---
title: "Users/Groups now showing after import"
date: 2010-02-10
forum: General Help
---

### Post by seanmccaskey on 2010-02-10
Imported users and groups (UIDs 500 and above) from Redhad to Ubuntu 9.10 by appending users to the passwd, shadow and group files. Users and groups appear to work, but they do not show in the Users/Groups GUI. Is that because they do not start at a UID 1000 and up? What are my options to make them visable?
 
Thanks!
 
-Sean

---

### Post by jken146 on 2010-02-10
Yeah, they have to have uid >= 1000

---

### Post by jken146 on 2010-02-10
You can use **usermod -u** to change the UID values.

---

### Post by sisco311 on 2010-02-10
In the /etc/login.defs file change the value of UID_MIN from 1000 to 500.

[https://bugs.launchpad.net/ubuntu/+source/gdm/+bug/247910](https://bugs.launchpad.net/ubuntu/+source/gdm/+bug/247910)

---

### Post by seanmccaskey on 2010-02-10
Multiple ways to fix in less then an hour... Great job.  Thanks!!

---

