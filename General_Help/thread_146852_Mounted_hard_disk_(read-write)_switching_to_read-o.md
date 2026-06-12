---
title: "Mounted hard disk (read-write) switching to read-only after some time"
date: 2006-03-19
forum: General Help
---

### Post by Pixilarion on 2006-03-19
I'm having a strange problem: In fstab I mount my second hard drive (/dev/hdb1) as rw. Everything works fine: I can write to it, read from it, etc. But after some time, let's say 1-2 days (it is a server that is always on), it suddenly switches into read-only mode for a reason I haven't been able to discover yet. When I try to copy something to the hard drive it says "Read-only filesystem".

I don't understand what is going on...

Any ideas?

TIA!
Pixilarion

```

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda1       /               ext3    defaults,errors=remount-ro 0       1
/dev/hda5       none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0
/dev/hdb1       /mnt/HD80       ext3    rw,user,auto,exec       0       0

```

---

### Post by Pixilarion on 2007-01-06
After all, it seemed like the hard disk was broken, so nothing could help te poor thing. :) I replaced the disk with a new one, and all works perfectly.

---

