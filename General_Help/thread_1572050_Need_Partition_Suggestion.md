---
title: "Need Partition Suggestion"
date: 2010-09-10
forum: General Help
---

### Post by Blue-Fox on 2010-09-10
A newbie to linux os needing some help with partitioning my hard drive. 

hp laptop that is several years old with **1gb ram**.

Installed a new 320GB hard drive and installed **windows xp home** on the first 1/2 of the drive. using the NTFS format. The remainder of the drive is unformated.

I would like to use the remainder of the hard drive to install **Ubuntu 10.04.1 LTS.**

After reading many of the discussions about Partitioning I became a little confused as to 


[LIST=1]
[*]the best number of partitons
[*]size of partitions
[*]type of partitions
[*]placement of partitions
[*]naming the partitions
[/LIST]
If possible there may be some files that I would like to use with both windows and linux. Like photos or other files. Not sure what all is possible, however I don't really want to run ubuntu from inside windows.

Boot time and speed of executing programs is of importance to me.

Your suggestions are greatly appreciated.

---

### Post by Rubi1200 on 2010-09-10
Personally, I recommend going with the default installation options which will create a / partition (which includes /home) and a swap partition on an extended partition (depends on how much RAM you have but usually twice the amount i.e. 1GB RAM = 2GB swap).

If you want to share files, you could create a separate partition and format it to FAT32 (recognized by both Windows and Ubuntu).

Summary:

160GB Windows XP NTFS
120GB Ubuntu Ext4
40GB Shared Data FAT32

Of course, you could make the shared partition larger or smaller depending on your needs.

Hope this helps.

---

### Post by Blue-Fox on 2010-09-10
Thank you for your reply. So the default instillation will automatically create a home and swap partition. 

Will I need to designate the size of the swap partition? 

Will the default instillation place the partitions where they work the best? 

All this is new to me.

---

### Post by perspectoff on 2010-09-10
You really don't have to do anything tricky at all. 

Let's say you have a 160 Gb partition for Windows XP and the rest is free space on the hard drive.

Simply pop in the Ubuntu LiveCD and let it automatically use all the remaining free space to install the ubuntu OS. It will create a swap partition and the Ubuntu root partition for you automatically. You won't have to do anything manually at all.

Ubuntu can share files with Windows already. Nothing special to do. 

As a newbie, I just wouldn't fiddle with multiple partitions. 

Now, if you already have Windows XP installed on the entire 320 Gb hard drive, you will have to shrink it first. If you use Windows frequently, give it at least 100 Gb (160 Gb is great).

I happend to live GParted LiveCD as a partition manager, but most of partition management can also be done using the Partition manager included on the Ubuntu LiveCD.

But, if your intent is to eventually be a guru and play with multiple (more than 2) OSs on your hard drive, here is my suggestion (which takes quite a bit of effort in the beginning but is worth it in the long haul):

[http://ubuntuguide.org/wiki/Multiple_OS_Installation](http://ubuntuguide.org/wiki/Multiple_OS_Installation)

---

### Post by Blue-Fox on 2010-09-10
Thank you both for your help, it is greatly appreciated.
):P

---

### Post by deserthowler on 2010-09-10
In my experience, I'd set up a Fat32 partition of about 100 GB for files like music, video, shared documents, etc using gparted.  I'd tell ubuntu to install on the unused space and let it figure out what it needs for swap.

This approach has been working for me for several versions of Ubuntu.

Earl

---

### Post by cj.surrusco on 2010-09-10
Also, keep in mind that FAT32 can only hold files up to 4GB; you won't be able to store any large DVD images, or large archives. You may want to set up an NTFS partition instead, Ubuntu is fully compatible with NTFS. Plus it supports large files over 4GB, and is faster than FAT32. Just make sure that the ntfsprogs package is installed.

---

### Post by deserthowler on 2010-09-10
> **cj.surrusco said:**
> Also, keep in mind that FAT32 can only hold files up to 4GB

Thanks for the reminder   :oops:  

Earl

---

### Post by perspectoff on 2010-09-10
> **deserthowler said:**
> In my experience, I'd set up a Fat32 partition of about 100 GB for files like music, video, shared documents, etc using gparted.  I'd tell ubuntu to install on the unused space and let it figure out what it needs for swap.

This approach has been working for me for several versions of Ubuntu.

Earl

I thought the limit of a FAT32 partition was 32 Gb (at least for Windows 2000 and similar systems). I realize this isn't the theoretical maximum, but can Windows Vista and Windows 7, for example, recognize FAT32 drives greater than 32Gb?

Also, don't FAT32 Gb drives have a filesize maximum of 2 Gb? This makes it unusable for movies, etc. that are routinely 4 Gb or greater.

I stopped using FAT32 for this reason.

---

### Post by cj.surrusco on 2010-09-10
> **perspectoff said:**
> I thought the limit of a FAT32 partition was 32 Gb (at least for Windows 2000 and similar systems). I realize this isn't the theoretical maximum, but can Windows Vista and Windows 7, for example, recognize FAT32 drives greater than 32Gb?

Also, don't FAT32 Gb drives have a filesize maximum of 2 Gb? This makes it unusable for movies, etc. that are routinely 4 Gb or greater.

I stopped using FAT32 for this reason.

FAT32 can support up to 8TB partitions if the cluster size is bumped up to 32KB. 

And the max file size is 4GB, not 2GB.

---

