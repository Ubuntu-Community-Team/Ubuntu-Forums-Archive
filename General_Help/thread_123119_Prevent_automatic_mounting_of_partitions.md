---
title: "Prevent automatic mounting of partitions"
date: 2006-01-29
forum: General Help
---

### Post by justask on 2006-01-29
How do I prevent Ubuntu automatically mounting certain partitions?

This is the content of my fstab:

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda4       /               ext3    defaults,errors=remount-ro 0       1
/dev/hda7       /home           ext3    defaults        0       2
/dev/hda1       /media/hda1     ntfs    defaults        0       0
/dev/hda3       /media/hda3     vfat    defaults        0       0
/dev/hda5       /media/hda5     ntfs    defaults        0       0
/dev/hda6       /media/hda6     vfat    defaults        0       0
/dev/hda8       none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0

/dev/hda1 is windowsxp install partition; I don't want it to be mounted at all
/dev/hda3 is a recovery partition; I don't want this mounted either

/dev/hda5 is an ntfs windowsdata partition I want to mount as /windata (read-only)
/dev/hda6 is a fat32 partition I want mounted as /sharedstuff (read/write)

Currently all four are automatically mounted at each logon.

Thanks

---

### Post by bartbes on 2006-01-29
It's easy. Comment out hda1 and hda3 by the other 2 just change the dirs, do ```
 sudo mount -a 
``` when you're done and you're done. **Make sure that you have already made the dirs (/windata and /sharedstuff)** ntfs is always ro and fat32 is already mounted rw (just defaults)

---

### Post by lha on 2006-01-29
[QUOTE=justask]How do I prevent Ubuntu automatically mounting certain partitions?

This is the content of my fstab:

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda4       /               ext3    defaults,errors=remount-ro 0       1
/dev/hda7       /home           ext3    defaults        0       2
/dev/hda1       /media/hda1     ntfs    defaults        0       0
/dev/hda3       /media/hda3     vfat    defaults        0       0
/dev/hda5       /media/hda5     ntfs    defaults        0       0
/dev/hda6       /media/hda6     vfat    defaults        0       0
/dev/hda8       none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0

/dev/hda1 is windowsxp install partition; I don't want it to be mounted at all
/dev/hda3 is a recovery partition; I don't want this mounted either

/dev/hda5 is an ntfs windowsdata partition I want to mount as /windata (read-only)
/dev/hda6 is a fat32 partition I want mounted as /sharedstuff (read/write)

Currently all four are automatically mounted at each logon.

Thanks[/QUOTE]

Use noauto and comment out some lines or remove them. Like this:
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda4       /               ext3    defaults,errors=remount-ro 0       1
/dev/hda7       /home           ext3    defaults        0       2
**#**/dev/hda1       /media/hda1     ntfs    defaults        0       0
**#**/dev/hda3       /media/hda3     vfat    defaults        0       0
/dev/hda5       /media/hda5     ntfs    **noauto**        0       0
/dev/hda6       /media/hda6     vfat    **noauto**        0       0
/dev/hda8       none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0

Those lines with a '#' can be removed if you want to, but they may prove useful if you want to mount those partitions some time. You could also replace 'defaults' with 'noauto', like I did for hda5 and hda6.

---

### Post by justask on 2006-01-29
Thanks. I wasn't sure I could just comment them out.

---

