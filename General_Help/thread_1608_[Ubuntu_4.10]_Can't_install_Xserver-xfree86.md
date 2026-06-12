---
title: "[Ubuntu 4.10] Can't install Xserver-xfree86"
date: 2004-10-22
forum: General Help
---

### Post by blade181 on 2004-10-22
When i try to install ubuntu-desktop at the end of the second stage of the installation process it just won't the package xserver-xfree86. It somehow won't execute the script inside the package. I allready tried the package from a debian unstable release but that won't do either.

So when i try to install this package i only see preconfiguring the package and then it stops. What could be the problem?

I installed ubuntu from the ISO cd, 4.10.

---

### Post by daniels on 2004-10-22
Unfortunately, we'd need the exact output to debug this any further.

---

### Post by blade181 on 2004-10-22
What can i give you then? There is very little to log, i tried to execute dpkg --force-all -D2 -i xserver-xfree86. This resulted in a hang at the preinst script. I will give you the log of dpkg soon.

HARDWARE:
Athlon-XP 2400+ 266FSB
512 MB RAM
Maxter 60 GB 7200tr
Reiserfs partition 6 GB

---

### Post by ReddoC on 2004-11-12
I have exactly the same problem ! 

I can't find any help about this.

---

### Post by wallijonn on 2004-11-13
maybe the .iso is faulty. did you run md5checker against the md5 file?

---

### Post by daniels on 2004-11-13
[QUOTE=wallijonn]maybe the .iso is faulty. did you run md5checker against the md5 file?[/QUOTE]Sounds like discover's dying to me.  Three reports of this in a day after none previously -- hmmm.

---

