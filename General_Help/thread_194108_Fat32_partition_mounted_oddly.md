---
title: "Fat32 partition mounted oddly"
date: 2006-06-11
forum: General Help
---

### Post by notquitehere188 on 2006-06-11
i have a 44 GB fat32 partition on /dev/hdb9, but when i enabled it its acess path became /boot, and when i try to change the access path to /media/hdb9 in the discs program, it does not work, when i go to that folder (/media/hdb9) however it shows nothing and says 8.3 GB free, which is the free space on my main system partition on hdb8, i am confused.  Is it ok to leave it in /boot or does that folder have some signifigance

---

### Post by aysiu on 2006-06-11
/boot has quite a bit of significance, as that's what allows you to... boot to Ubuntu.

For mounting Windows partitions properly, go here:
[http://www.psychocats.net/ubuntu/mountwindows](http://www.psychocats.net/ubuntu/mountwindows)

---

