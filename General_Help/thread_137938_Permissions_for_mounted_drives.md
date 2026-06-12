---
title: "Permissions for mounted drives"
date: 2006-02-28
forum: General Help
---

### Post by mackinax on 2006-02-28
All of my drives & partitions were detected and are mounted. But I don't have permission to access any drives except for one FAT32 partition (hdb7) on the same physical drive as my ubuntu install (hdb). And that one is read-only.

```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hdb1       /               ext3    defaults,errors=remount-ro 0       1
/dev/hdb6       /home           ext3    defaults        0       2
/dev/hda1       /media/hda1     ntfs    defaults        0       0
/dev/hda5       /media/hda5     ntfs    defaults        0       0
/dev/hda6       /media/hda6     ntfs    defaults        0       0
/dev/hda7       /media/hda7     ntfs    defaults        0       0
/dev/hda8       /media/hda8     ntfs    defaults        0       0
/dev/hdb7       /media/hdb7     vfat    defaults        0       0
/dev/hdc1       /media/hdc1     ntfs    defaults        0       0
/dev/hdc2       /media/hdc2     ntfs    defaults        0       0
/dev/hdc3       /media/hdc3     ntfs    defaults        0       0
/dev/hdb5       none            swap    sw              0       0
/dev/hdd        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0
```

I would like to have **read-only** permission for my **ntfs** drives, and **read & write** permission for the **FAT32** (vfat) drive. 

Thank you!

---

### Post by RAOF on 2006-03-01
Because neither ntfs or fat32 have linux permissions support, the "defaults" option leaves everything owned by root and inaccessible to everyone else.

You want to change "defaults" to
```
defaults,umask=0000
``` for your FAT32 drives (which will give read/write/execute permissions), and ```
defaults,umask=0222
``` which will give read/execute permission for you NTFS drives.

Actually, you could use the same umask for both - the Ubuntu NTFS kernel driver is built without the (experimental) write-support turned on, so you'll never be able to write to it, no matter how hard you try ;)

---

### Post by mackinax on 2006-03-01
That helped. Thank you!

---

