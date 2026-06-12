---
title: "upgrade 8.04 directly to 9.10"
date: 2010-04-26
forum: General Help
---

### Post by Qiao on 2010-04-26
Is it possible to upgrade 8.04 directly to 9.10 without 8.10 and 9.04 ?  

All manuals said that i should pass all version, but I don't want, because it will take too long.  

What is the best way? Just burn 9.10 and install it without thinking?

---

### Post by zvacet on 2010-04-26
No,it is not possible to upgrade from Hardy to Karmic directly.But,you have even better choice,you can directly upgrade from Hardy to lucid because both of them are LTS resleases.So,wait for couple of days and make direct upgrade.

---

### Post by Qiao on 2010-04-26
But what will happen if I burn 9.10 and install it on 8.04 ? As a new system. 
I am downloading it now.


Waiting is very hard. Near impossible. Have not use ubuntu for more than year.

---

### Post by 3rdalbum on 2010-04-26
What with a couple of days until 10.04 is released, you could do the upgrade right now and it should be safe. Make sure that System > Administration > Software Sources is set to notify for new LTS releases only, and then run this command:

```
gksudo "update-manager -d"
```

You should be notified (perhaps after hitting the Check button) that Ubuntu 10.04 is available and you can upgrade.

Alternatively, if you really want to do a clean install, don't bother downloading 9.10. Just download 10.04 now (which will be a release candidate), install it and run Update Manager on April 30.

---

