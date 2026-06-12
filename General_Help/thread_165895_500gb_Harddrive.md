---
title: "500gb Harddrive"
date: 2006-04-25
forum: General Help
---

### Post by riscostm on 2006-04-25
Hi guys,

Just installed ubuntu and previously had windows xp installed.  I've got an external 500gb harddrive formatted as ntfs.  What is the best format to use in ubuntu?? Its all one partition and its used for sharing music, media files etc.....

cheers,
Johno - RiscosTM

P.S Correct me if I'm wrong but I'm I right in saying Ubuntu can only read an ntfs partition??? And is there away of converting this drive to a linux partition with out effecting the data on the drive?????   I do have a backup of the data tho!!](*,)

---

### Post by rabidphage on 2006-04-25
fat32 would be fine and most os's wouldn't have problem accessing it.
don't know about the converting though. You can alway try resizing it. anyway fat32 is not good with big volume as well. So in my opinion your choices are very few. resizing and assorted tinkering always entail potential data loss. so there we have it

---

### Post by aysiu on 2006-04-25
[QUOTE=riscostm]
Just installed ubuntu and previously had windows xp installed.  I've got an external 500gb harddrive formatted as ntfs.  What is the best format to use in ubuntu??[/quote] Ext3, but if you're ever planning to use that external hard drive with a Windows computer, you should create at least part of that 500 GB to be FAT32. > Its all one partition and its used for sharing music, media files etc..... Sharing between your Windows and Ubuntu partitions or sharing between various computers (yours and other people's)?

> 
P.S Correct me if I'm wrong but I'm I right in saying Ubuntu can only read an ntfs partition??? Yes, NTFS is effectively read-only if you care about the data. > And is there away of converting this drive to a linux partition with out effecting the data on the drive?????   I do have a backup of the data tho!!](*,) No. But you can resize it and create a new Linux partition within the drive (500 GB is **a lot of space**). Go to Applications > Accessories > Terminal and copy and paste these commands: ```
sudo apt-get update
sudo apt-get install gparted ntfsprogs
sudo fdisk -l
``` Look for your external hard drive's device--let's just say it's /dev/sda1 for the sake of this example. ```
sudo umount /dev/sda1
``` The hard drive **must** be umounted before it can be repartitioned. ```
sudo gparted
``` Resize and create a new Ext3 partition.

---

