---
title: "WTF How did my MBR go poof over night"
date: 2011-08-09
forum: General Help
---

### Post by pqwoerituytrueiwoq on 2011-08-09
I am using legacy grub i easily fixed my MBR but how did it vanish on me
I attached boot script info results the 1st one is before i fixed is the second is after
i would like to know why/how it went poof
anyone know how to remove the MBR on /dev/sdb

---

### Post by ajgreeny on 2011-08-09
I have no idea how your mbr disappeared, nor how to delete the mbr from sdb, but you could simply install grub to the mbr of sdb, as well as sda to replace what is there at the moment, and you will then have a sort of backup.  Just change the boot priority if it happens again and grub will go to work from the second disk.

---

### Post by pqwoerituytrueiwoq on 2011-08-09
nice idea about setting the MBR on sdb to boot root on sda :)

---

