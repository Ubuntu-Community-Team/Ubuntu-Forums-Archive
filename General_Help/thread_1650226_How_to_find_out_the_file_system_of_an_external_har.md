---
title: "How to find out the file system of an external hard disc?"
date: 2010-12-21
forum: General Help
---

### Post by pstein on 2010-12-21
Assume I have plugged in an external USB hard disc.
 
How can I find out the file system (ext2, ext3, reiserfs,...) of this hard disc?
 
Peter

---

### Post by Verbeck on 2010-12-21
from a terminal, run 
```
sudo blkid -c /dev/null
or
sudo fdisk -l
```edit: or use system>administration>disk utility

---

### Post by 3Miro on 2010-12-21
You can install Gparted. When you start it, it will give you information on how all disks have been partitioned and formated. Gparted is in the software center, don't make changes using it, just read the information, if you make changes you may lose all data from whatever disk you changed.

---

### Post by dandnsmith on 2010-12-21
I concur with using gparted, since it's built in to the distros nowadays. fdisk -l doesn't show how what sort of filesystem there is (I firmly believe), as my ext3 filesystems show as ext2 in fdisk.

---

