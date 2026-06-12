---
title: "Problem with win7 64 bit when install ubuntu in the same partition"
date: 2010-12-07
forum: General Help
---

### Post by thexnightmare on 2010-12-07
Dear,
After my installation of ubuntu on the same partition where I have Windows 7 64 bit, the windows 7 encourage alot of problems, and ubuntu refusr to be uninstalled to reinstall it in another partition.
How can I solve this?
BTW, ubuntu works fine alone when choosing it form boot manager.
Thx

---

### Post by piratebill on 2010-12-07
So, if I read this right, you overwrote your windows partition to install ubuntu?

---

### Post by thexnightmare on 2010-12-07
I think  so.
I was using win7 x64 on my c drive.
i enserted ubuntu dvd, choosed second option to install ubuntu as a software inside windows to be able to remove it as normal program, and finished the installation and now I have this problem.
Plz help me in deleting it to be able to reinstall it in a clean partition without loosing win7 ana c drive data.

---

### Post by piratebill on 2010-12-07
as for uninstalling it, I have no experience with wubi (the installer).  For installing it on another partition I can help.  First things first, have you backed up your data?

---

### Post by bcbc on 2010-12-07
[https://wiki.ubuntu.com/WubiGuide#Uninstallation](https://wiki.ubuntu.com/WubiGuide#Uninstallation)

Uninstalling will delete all data/settings you have currently on Ubuntu

---

### Post by thexnightmare on 2010-12-08
No problem to loose all ubuntu things, as all what I want to not loosing vista things

---

### Post by thexnightmare on 2010-12-08
BTW, I realised something.
In windows7 I have:
- C & D (Raid 0 from 2 hard disks)
- E & F ( 2 separate hard disks)
In ubuntu I found just these in Places menu:
- Systen reserved
- Labels of (E &F).
Does ubuntu can't recognized raid0 partitions?

---

### Post by thexnightmare on 2010-12-08
Finally i get the solution.
I made a chkdsk for the drive c and after finishing and restarting I be able to uninstall it, and all things are fixed now.
I will install it to d drive, but, do u suggest to install it form windows or boot from cd when restarting?
Thx

---

