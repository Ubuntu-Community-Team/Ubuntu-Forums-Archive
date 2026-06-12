---
title: "Can't resize partition"
date: 2012-06-22
forum: General Help
---

### Post by pashkypreos on 2012-06-22
My hard drive is partitioned as follows:

/dev/sda1 - FAT32
/dev/sda2 - ntfs
/dev/sda3 - extended
[INDENT]/dev/sda5 - ntfs[/INDENT]
[INDENT]/dev/sda6 - ext4[/INDENT]
[INDENT]/dev/sda7 - linux swap[/INDENT]

sda5, sda6 and sda7 are part of the extended partition

I boot in an Ubuntu live CD and start gparted as super user.  I use 'swap off' for /dev/sda7 and I attempt to resize /dev/sda5 but I get an error.  When I look at the details, it seems that the error occurs during the ntfresize command.  I dont know what the error is exactly, near the end of the output of the ntfsresize command i see:

"Are you sure you want to proceed (y/[n])? OK quitting. NO CHANGES have been made to you NTFS volume"

Anything that I might be doing wrong?

---

### Post by dino99 on 2012-06-22
generally speaking, its better to re-use the same tool to tweak a partition; meaning that if that ntfs partition have been set with the windows tool, then resize/shrink it with the same tool.

otherwise you should not get error if a partition respect the other ones (not hovering), but maybe you need to sart resizing sda3 first.

---

### Post by florus on 2012-06-22
> **pashkypreos said:**
> 

"Are you sure you want to proceed (y/[n])? OK quitting. NO CHANGES have been made to you NTFS volume"

Anything that I might be doing wrong?

You are typing y to accept the change, I presume? Otherwise the default choice n (=no) will operate.

---

### Post by sudodus on 2012-06-22
Editing partitions is risky, so I suggest that you start the process by ***backing up*** at least all your personal data, but to be on the safe side, make an image or clone of the whole drive.

Then ***defragment*** the ntfs partition. That will move the file data in such a way that it will be easier (or possible) to shrink the partition.

If you want to expand it, you have to shrink an adjacent partition.

If still no luck, and you rely on your backup, then you can wipe the ntfs file system and its partition. Then make new partitions or resize/move the neighbor partition(s).

---

### Post by wilee-nilee on 2012-06-22
Post a screen shot of gparted looking at the HD, use the paperclip in the reply panel to post it.

Tell as well what is in the NTFS in the extended, whether a OS or data mainly.

---

### Post by Mark Phelps on 2012-06-23
Google for MiniTool Partition Wizard Boot CD.  That is a free MS Windows app that does partitioning.  Burn it to CD and boot from it.  Use that to make changes to any NTFS partitions.

---

