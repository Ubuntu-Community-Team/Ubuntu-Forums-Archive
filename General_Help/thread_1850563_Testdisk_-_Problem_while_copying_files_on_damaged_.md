---
title: "Testdisk - Problem while copying files on damaged partitions"
date: 2011-09-26
forum: General Help
---

### Post by sekiryou on 2011-09-26
Hi,

  Ok, here's my problem. The other day there was a storm and we lost electricity for 12 hours... When it came back, everything was ok but I notice my 160Gb HDD was missing (not mounted)... After many tries I wasn't able to make Ubuntu see it. I have ext4 and fat32 partitions on that HDD. Windows wasn't able to "mount" the Fat32 ones either (I don't know if you can say that in Windows?). Windows HDD manager was showing only one big 160Gb Fat32 partion. I thought that was weird so I checked back in Ubuntu, GParted and "Disk Utility" said the same, one big Fat32 partition. But when I checked for errors, both in Ubuntu and Windows, the disk is "healthy" no errors at all.

  Then, I decided to search for the missing partion with **testdisk**. This told me the superblock or my ext4 partion was missing/corrupted. That explains why I can't mount it. **testdisk** is able to see the partitions and the files on them, so I decided to copy everything on my empty external 1.5Tb disk. Everything is great execpt that now the folder where I'm copying my ext4 partion (140Gb) is now at 300Gb and counting... which is impossible since my entire HDD is only 160Gb !

  I'm beginning to worry a bit. Have I done something wrong?

---

### Post by sekiryou on 2011-09-26
*** UPDATE ***

Ok, testdisk have finished copying files... at 411.4 Gb... I'm still wondering what happened...

---

