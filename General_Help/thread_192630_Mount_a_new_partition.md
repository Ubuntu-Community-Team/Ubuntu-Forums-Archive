---
title: "Mount a new partition?"
date: 2006-06-09
forum: General Help
---

### Post by Cable on 2006-06-09
I just made a new partition on my hdd, and am having trouble mounting it.  When I right click and choose "Mount Volume", an error pops up saying "Unable to mount selected volume."  How do I mount this to make it usable??

---

### Post by aysiu on 2006-06-09
What filesystem is it--NTFS, FAT32, Ext3?

---

### Post by Cable on 2006-06-09
Ext3

---

### Post by aysiu on 2006-06-09
[QUOTE=Cable]Ext3[/QUOTE] Try this: [http://www.psychocats.net/ubuntu/mountlinux.html](http://www.psychocats.net/ubuntu/mountlinux.html)

---

### Post by Cable on 2006-06-09
Awesome, worked perfectly.  Thanks!  Now, I just have an NTFS partition I need to get some files off of, then I'm going to wipe it.  So, how would I mount it, then unmount it before formatting it?

---

### Post by aysiu on 2006-06-09
Assuming the NTFS partition is /dev/hda1... ```
sudo mkdir /recovery
sudo mount -t ntfs /dev/hda1 /recovery -o nls=utf8,umask=0222
``` Then, when you're done: ```
sudo umount /dev/hda1
sudo rmdir /recovery
```

---

