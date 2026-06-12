---
title: "How to mount a disk"
date: 2010-01-27
forum: General Help
---

### Post by titanicmusic14 on 2010-01-27
Ok I just installed my 1.5 TB drive. I used Gparted to format it as ext3 . why is it saying that the size is 1.36TB with 22.12Gib used and 1.34 TiB unused. How is it that I used the drive and all I did was install it. how should I reformat/format it.? I'm not putting an OS on it. Just media. thanks

Currently I have the file system as extended and then under it its ext3

---

### Post by t4thfavor on 2010-01-27
There is a descrepancy between Software folks, and hardware folks on the definition of a GB. 

Some say its 1000MB some say its 1024MB, we've been fighting this since it was 1024KB vs 1000KB. 

That's correct, as for the used space, I have no idea, anybody else chime in on that?

---

### Post by x33a on 2010-01-27
ext3 reserves 5 % of the total space for recovery. you can use tune2fs to reclaim the reserved space.

take a look here:

[http://wiki.archlinux.org/index.php/Ext3_Filesystem_Tips#Reclaim_Reserved_Filesystem_Space](http://wiki.archlinux.org/index.php/Ext3_Filesystem_Tips#Reclaim_Reserved_Filesystem_Space)

---

