---
title: "Non-destructively converting FAT32 to NTFS and such."
date: 2010-08-14
forum: General Help
---

### Post by MechWarrior001 on 2010-08-14
Hey, long time no see. Do you guys know how to non-destructively convert a FAT32 HDD into something generally better like NTFS or Ext2/3/4 and etc? Also, what filesystem would you recommend?

---

### Post by Dustin2128 on 2010-08-14
> **MechWarrior001 said:**
> Hey, long time no see. Do you guys know how to non-destructively convert a FAT32 HDD into something generally better like NTFS or Ext2/3/4 and etc? Also, what filesystem would you recommend?

I'd recommend EXT4. As for converting it without destroying files; I don't think that's possible. But if its an HDD still using FAT32, logic says that its an old hard drive, backing it up shouldn't be much of a problem.

---

### Post by MechWarrior001 on 2010-08-14
The problem is that it's 80GB, and the only thing I have bigger than that is a 160GB SATA drive, which I can't use due to my current system being IDE only. If its possible to compress the entire drive into one huge archive (I heard 7z and RAR are some really good ones, know any others?) I guess I could compress using the best method and store on the smaller 60GB I have then convert. Would that be practical? I don't think I have any other options at this moment.

---

### Post by bodhi.zazen on 2010-08-15
It can be done:

[http://www.ntfs.com/quest3.htm](http://www.ntfs.com/quest3.htm)

[http://support.microsoft.com/kb/307881](http://support.microsoft.com/kb/307881)

---

