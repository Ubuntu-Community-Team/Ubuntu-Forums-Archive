---
title: "world of warcraft problem"
date: 2009-09-23
forum: General Help
---

### Post by TAYLOR! on 2009-09-23
this is a copyied over insatllation of wow.

i use a ATI Radeon HD4890, some P4 cpu 4gbs of ram

i added

```
SET gxApi "opengl"
```to the config.wtf to sort the fps problem, it solved the fps but it left me with scrambled writing and whatever you see in the screen shot ive attached.

ive read that closing the mini map stops this but it just makes it lag as much as it did without the line added in config.wtf.

is there a way to fix the fps problem?

---

### Post by TAYLOR! on 2009-09-23
also i forgot to mention that im running 8.10

---

### Post by sedawk on 2009-09-23
Have you checked the application database of the wine project?

[http://appdb.winehq.org/objectManager.php?sClass=application&iId=1922](http://appdb.winehq.org/objectManager.php?sClass=application&iId=1922)

You might try and install a newer version of wine
(get source, compile, install to some non-default
place like directory /home/user/mywine and test
against that version.)

---

### Post by TAYLOR! on 2009-09-24
right ive sorted the scrambling letters problem, i used the drivers from the amd/ati site.

i still have the fps problem, and i went through a few things on that site (thx for the link btw)

aparently there are a load of fixes in the latest drivers but the 9.9 drivers wont install anything higher than 8.65 for some reason. so i upgraded from 8.10 to the lastest 9.04 distro, to see if its because it will only work on that cus of xserver/xorg versions or something. but still nothing higher than 8.65 version graphics drivers.

i do have the lastest version of Wine aswell, would it make a difference if i installed it in a non-default place ? ive just downloaded it from respositrys/snaptic.

---

