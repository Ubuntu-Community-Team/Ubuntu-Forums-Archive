---
title: "dd partition image to another partition"
date: 2012-07-02
forum: General Help
---

### Post by palek on 2012-07-02
Hello. I use Ubuntu 12.04 bootable flashdrive to recover my data as I have got an unmountable NTFS partition ([COLOR=#000000][FONT=Courier New]NTFS signature is missing)[/FONT][/COLOR] on the harddrive of my laptop. This partition was correctly seen by fdisk and copied  into an image file with ddrescue (no bad blocks were reported). 
Obtained image file can not be mounted too ([COLOR=#000000][FONT=Courier New]NTFS signature is missing)[/FONT][/COLOR]. 
I think about trying to dd that image file onto a free partition of another harddrive (and then pass windows chkdsk /f on it). 
I have the following questions: 
should the output partition be mounted or unmounted? 
Should it bear NTFS filesystem? Or the current filesystem of the partition will be "overwriten" by the copy of it in the image file?
Should it be of exact size as the image file or can it be larger than the image file? 
Is there a risk for the other partitions that are on the diskdrive I will dd the image onto?
Thank you in advance for your help.

---

### Post by cipherboy_loc on 2012-07-03
Sounds like you need to boot into windows and try and mount it there. Have you tried it? Linux cannot "recover" NTFS file systems, ie recover corrputed ones.


Cipherboy

---

### Post by palek on 2012-07-03
After I have discovered the problems with NTFS I have made the image of the partition with ddrescue and worked with the image then. My plan is to expand that image to another harddrive, where there is a free partition and then Windows will enter the game. If something goes wrong - well, I keep the original image of the partition intact in a safe place. I do not know well behaviour of dd utility, therefore, questions arise.
Of course, valuable advices of other recovery approaches and utilities etc are much appreciated.

---

### Post by David Andersson on 2012-07-03
> **palek said:**
> 
I think about trying to dd that image file onto a free partition of another harddrive (and then pass windows chkdsk /f on it). 
I have the following questions: 
should the output partition be mounted or unmounted?

The target partition must be unmounted. (A mounted file system would be very confused when blocks begin to change under it.)

> **palek said:**
> 
Should it bear NTFS filesystem? Or the current filesystem of the partition will be "overwriten" by the copy of it in the image file?

It will be overwritten. But the file system type is noted in the partition table, and will stay the same (unless you change it by other means). To make it easier for you, let the file system being written over be NTFS.

> **palek said:**
> 
Should it be of exact size as the image file or can it be larger than the image file?

I am not completely sure, but I think dd to a larger partition should work. The file system have tables of all its blocks, and the excess size would be unused. There is a chance fsck or something can detect that the partition is larger than the filesystem and try to expand its size, but I don't know.

> **palek said:**
> 
Is there a risk for the other partitions that are on the diskdrive I will dd the image onto?

If you dd to /dev/sdXY of a particular partition it should not be able to write into other partitions.

---

