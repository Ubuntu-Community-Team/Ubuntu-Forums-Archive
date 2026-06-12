---
title: "Pyrun.exe - no disk?"
date: 2010-11-25
forum: General Help
---

### Post by Danimal96 on 2010-11-25
Hello,

When I try to install Ubuntu with wubi.exe I get this error (It's in Dutch):

pyrun.exe - geen schijf

Er bevindt zich geen schijf in het station. Plaats een geschikt medium in station \Device\Harddisk2\DR3. 

DR3 was DR2 the first time I tried.

Thanks

---

### Post by searchfgold6789 on 2010-11-25
The reason you are getting this problem has to do with the fact that Python does not like external or empty drives.
Many people are getting this problem in Wubi 9.04+. The consensus is that it can be solved if you disconnect any empty CD drives, Mp3 players, iPods, USB flash drives, or multi-card readers, etc.
Ubuntu and windows will both detect and install them again.
Good luck,
 - search

---

