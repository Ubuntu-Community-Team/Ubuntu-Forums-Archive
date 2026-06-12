---
title: "Problems with external eSata hd: no LBA48 support???"
date: 2011-12-11
forum: General Help
---

### Post by ScarySquirrel on 2011-12-11
I'm tryinkz to recover dataz from Grandma's HDD. I pop-ped her dizk intos my external drive and hooked it up to my Leenooks laptop. 
I got the following output from TestDisk 6.11 : 

```

Disk /dev/sdd - 137 GB / 127 GiB - CHS 16709 255 63

The Harddisk size seems to be 137GB.
Support for 48-bit Logical Block Addressing (LBA) is needed to access
hard disks larger than 137 GB.

...

[ Continue ]  The HD is really 137 GB only.
[ Quit     ]  The HD is bigger, it's safer to enable LBA48 support first.

```

By the dubz, here is my output from $ uname --all : 

Linux Lock 2.6.38-8-generic #42-Ubuntu SMP Mon Apr 11 03:31:50 UTC 2011 i686 i686 i386 GNU/Linux

LBA48 SUPPORT ... I CAN HAZ????!!!!!???!?

---

