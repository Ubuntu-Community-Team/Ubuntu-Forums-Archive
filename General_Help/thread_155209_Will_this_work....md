---
title: "Will this work..."
date: 2006-04-04
forum: General Help
---

### Post by harrisale on 2006-04-04
Hello, 

I recently deleted my Windows XP NTFS partition. I re-wrote the partition table with TestDisk and the partition is back (can be viewed in fdisk), accept that I can't access it. I now only have Linux (props to Linus) This is what I get when trying to boot WinXP:
```
GRUB Error 13: Invalid or unsupported executable format
```

When trying to mount it, I get:
```
mount: wrong fs type, bad option, bad superblock on /dev/hda2,
       missing codepage or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so 
```

[SIZE=2]This is what I would like to know:[/SIZE]

I suspect the drive is unaccessable because there is no or a corrupt book sector

Would booting into the recovery console on the Win XP disk and then running **fixmbr** and **fixboot** fix my problems?

thanx,

=harrisale+

---

### Post by az on 2006-04-04
It looks like TestDisk didn't do a good job.

You can try parted.  Delete the partition and then "rescue" it.  Maybe that will make a proper entry in the partition table for it.

---

