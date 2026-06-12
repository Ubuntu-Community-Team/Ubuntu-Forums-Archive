---
title: "Which File System for only files"
date: 2009-10-13
forum: General Help
---

### Post by El Raspa on 2009-10-13
Hello

I'm going to remove completly windows from my laptop and I'm going to rebuild the HD Partitions

I want to have 4 partitions

1. ext4 for /
2. ext4 for /home
3. swap for swap :P
4. ???? for files (videos, music, ISO images, etc)

So, Which file system is better for the fourth partition, ext3, ext4 or NTFS???

I usually work with ISO images of 4 and 8 Gb

Thanks

---

### Post by rampageoberon on 2009-10-13
> **El Raspa said:**
> Hello

I'm going to remove completly windows from my laptop and I'm going to rebuild the HD Partitions

I want to have 4 partitions

1. ext4 for /
2. ext4 for /home
3. swap for swap :P
4. ???? for files (videos, music, ISO images, etc)

So, Which file system is better for the fourth partition, ext3, ext4 or NTFS???

I usually work with ISO images of 4 and 8 Gb

Thanks

In my view any of those partitions will work. However my preference would be ext4/ext3 being the native filesystems for Linux.

NTFS will work too as NTFS-3G drivers are now stable.

---

### Post by ibuclaw on 2009-10-13
> **El Raspa said:**
> Hello

I'm going to remove completly windows from my laptop and I'm going to rebuild the HD Partitions

I want to have 4 partitions

1. ext4 for /
2. ext4 for /home
3. swap for swap :P
4. ???? for files (videos, music, ISO images, etc)

So, Which file system is better for the fourth partition, ext3, ext4 or NTFS???

I usually work with ISO images of 4 and 8 Gb

Thanks

Being the legacy user I am, I admire ext4 is blazing fast in comparison, but I'd rather ext3 for mission critical data.

ext4 for /
ext3 for /home
swapfs for swap
ext3 for /media/data

Regards
Iain

---

### Post by uberg on 2009-10-13
I would think that ext4 would be alright for your needs.  Although ext4 is just now becoming the standard on most Linux Distros it is a continuation of ext3 which has a long history of stability.  There are other file systems like ReiserFS and XFS that are arguably better at handling larger files, unless you really want to learn about file systems I would stick with the standard that is most widely used.

---

### Post by El Raspa on 2009-10-14
Thanks a lot for your help, I have discarded NTFS and will wait to see the new bugs of ext4

Thanks

---

