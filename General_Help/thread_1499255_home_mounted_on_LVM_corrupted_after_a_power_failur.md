---
title: "/home mounted on LVM corrupted after a power failure"
date: 2010-06-01
forum: General Help
---

### Post by nsupathy on 2010-06-01
Hello,

After a power failure, all the file systems came up fine except /home.  This is on the first logical volume of the only volume group I have on the system.  The other LVs mounted and seem to be fine.  Its running 64bit Karmic Koala.

It gives me 
/dev/vg0/lv01: read failed after 0 of 4096 at 0: Input/output error

I tried fsck.  The pvscan throws lot of error and finally ends up with the above error.

Is there any chance of recovering this file system?  Should I have to throw away this disk?  its only few months old WD disk.

Thanks.  Any help much appreciated.

-Umapathy

---

