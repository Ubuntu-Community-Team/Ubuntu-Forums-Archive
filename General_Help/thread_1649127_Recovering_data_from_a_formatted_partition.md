---
title: "Recovering data from a formatted partition"
date: 2010-12-19
forum: General Help
---

### Post by augied on 2010-12-19
Hi, I've asked about this in the installation section, but I decided here might be more appropriate.

I just installed kubuntu 10.10, replacing an older installation.  I have three hard drives one of which had all of the data I wanted to save, about 500gb.  I repartitioned and formatted the other two drives and made sure that the data drive would be mounted but not formatted.  When I booted into my new installation, the data drive was blank.  I'm not sure if it's relevant, but I had just upgraded the file system from ext2 to ext4 before starting the installation.

I've been trying to recover my lost partition with testdisk.  The website has instructions for recovering a formatted partition.  It looks like it's working until the instructions tell me to choose Boot and RebuildBS, which I don't see as options.

Can anyone give me any advice on how to recover?  How did this even happen?  Has anyone had a similar issue with installation?
Please help me,
Augie

---

### Post by augied on 2010-12-22
Update:
I'm working on a backup made with gddrescue onto an identical drive.  I've managed to mount the partition using a backup superblock.
```
sudo mount -o sb=131072 /dev/sdd1 /mnt/sdd1
```
df -h now shows the disk usage as 561G which is correct.  However, I can't see any files.

Now what?

---

