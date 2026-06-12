---
title: "USB HDD - NTFS Partition Dead after Ubuntu"
date: 2011-08-12
forum: General Help
---

### Post by SV5FRZ on 2011-08-12
Hi everyone,
This is my first post in this forum and I hope I posted in the right category.
This is the second time that this problem happens to me so I thought I'd check and see.

I own a local tech support business and I use Ubuntu Desktop's Live CD to backup files from all kinds of problematic / infected Windows installations and hard drives.
I boot from the CD, I go to Try Ubuntu and when it's ready, I plug in one of my USB HDDs to which I dump all the files from the customer's hard drive. (So that I can format it later)

The first problem happened last week. I backed up some stuff, and then windows saw the USB HDD as unformatted. I booted from Ubuntu again and it read the drive.

Yesterday I had a worse case of this problem, Ubuntu found an unformatted drive too... So I couldn't get to the files even though Ubuntu saw the partition was half full.

I remember my exact moves when yesterday's problem happened but I'm not sure if that could be the cause.
1. I always plug the USB drive AFTER Ubuntu has finished loading.
2. This is the first time that I did NOT safely remove the drive before shutting down, but instead, I completely shut down Ubuntu and the computer before unplugging the USB Drive. The computer was completely OFF when I unplugged it.
(My usual procedure is to Safely Remove first, and then shutdown)

I used data recovery software to get the files out of the drive, but I'd like to know if there's something I could've done to fix that partition without having to go that far.

Thanks for your help.

---

### Post by westie457 on 2011-08-12
> **SV5FRZ said:**
> Hi everyone,
This is my first post in this forum and I hope I posted in the right category.
This is the second time that this problem happens to me so I thought I'd check and see.

I own a local tech support business and I use Ubuntu Desktop's Live CD to backup files from all kinds of problematic / infected Windows installations and hard drives.
I boot from the CD, I go to Try Ubuntu and when it's ready, I plug in one of my USB HDDs to which I dump all the files from the customer's hard drive. (So that I can format it later)

The first problem happened last week. I backed up some stuff, and then windows saw the USB HDD as unformatted. I booted from Ubuntu again and it read the drive.

Yesterday I had a worse case of this problem, Ubuntu found an unformatted drive too... So I couldn't get to the files even though Ubuntu saw the partition was half full.

I remember my exact moves when yesterday's problem happened but I'm not sure if that could be the cause.
1. I always plug the USB drive AFTER Ubuntu has finished loading.
2. This is the first time that I did NOT safely remove the drive before shutting down, but instead, I completely shut down Ubuntu and the computer before unplugging the USB Drive. The computer was completely OFF when I unplugged it.
(My usual procedure is to Safely Remove first, and then shutdown)

I used data recovery software to get the files out of the drive, but I'd like to know if there's something I could've done to fix that partition without having to go that far.

Thanks for your help.

Hi and welcome to the Forums.

Next time you forget to unplug a USB drive before shutting down make sure it is plugged in for the next boot, sometimes that can prevent the situation you have.

If that does not cure it, run Gparted from the LiveCD and run a file-system check. That might cure the problem.

If not then still running the LiveCD go to the following link, download and run testdisk. This will recover your lost partitions. [http://www.cgsecurity.org/wiki/TestDisk](http://www.cgsecurity.org/wiki/TestDisk)

---

### Post by SV5FRZ on 2011-08-12
Thanks for the information.

I'm trying out TestDisk right now.

I'll make sure I safely remove every time just like I've been doing in it all along.

---

### Post by SV5FRZ on 2011-08-12
It's all fixed now.
TestDisk didn't do much.

I found a program called EaseUS Partition Master 9.0 Home Edition.
It was a free download so I tried it out.
Turns out chkdsk.exe fixed the problem after being called by the EaseUS software.

I had tried running check disk previously but windows couldn't work with an unformatted partition...
Now that the software called it, it went right through the drive and fixed all the indexes.
I'm copying the files back to the customer's formatted PC right now.

Thanks for all your help.

---

