---
title: "wipe a USB flash"
date: 2010-08-10
forum: General Help
---

### Post by TomAbada on 2010-08-10
hi all

i need a way to wipe my USB flash drive 
but i dont know of any wipe program that does that
can anyone tell me of a good way to wipe ? (prefer using the command line)

---

### Post by TeoBigusGeekus on 2010-08-10
gparted (partition editor)
Just format it as fat32.

---

### Post by oldfred on 2010-08-10
This will work. But is dangerous as if you type in the wrong drive you destroy your good data. double check everything before hitting enter.

with the flash drive plugged in to see which device it is.
sudo fdisk -l   If it is /dev/sdb, now use dd to wipe it of all data, partitions, and MBR information with command: 
dd if=/dev/zero of=/dev/sdb.

Also random is slow
[http://ubuntuforums.org/showthread.php?t=762420](http://ubuntuforums.org/showthread.php?t=762420)

There is also the shred command - more info
man shred

---

