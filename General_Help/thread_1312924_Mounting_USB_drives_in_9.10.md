---
title: "Mounting USB drives in 9.10"
date: 2009-11-03
forum: General Help
---

### Post by sreilly on 2009-11-03
I have just installed 9.10 on my Acer Aspire One A150 and it all works out of the box (thus far) - BRILLIANT!!

When I attach my WD 320G USB drive (which has an Ext3 and FAT32 partition) the drive names are mounted with lengthy character names (/media/4AD5-8742 and /media/d69b4f19-2a04-4fd5-9d4c-cd7d17eeffd4) rather than the /media/disk and /media/disk-1 of Jaunty.

My SD Card and Corsiar USB stick show the correct names.

Any ideas how to fix this?

Steve

---

### Post by michy99 on 2009-11-03
Looks like it is using the UUIDs to name the mount points. I am guessing that these partitions don't have labels. Try labeling them (I think gparted can do this) and see if they mount using the labels instead.

---

