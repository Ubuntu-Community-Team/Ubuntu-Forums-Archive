---
title: "Partition Help"
date: 2012-06-26
forum: General Help
---

### Post by Delarth on 2012-06-26
I am currently running Ubuntu server version 12.04 as a headless server. I have a secondary hard drive which is a single 3TB partition. What I want to do is shrink this partition down and then add a second partition to the drive. I have tried looking around for any guides or help on how to go about this but most places just talk about gparted or using a live CD. I do not have a way to use a live CD on the server for the time being so I am only able to do things from the command line.

I ran across mention of using ntfsresize but the manual talks about deleting the partition and recreating with the smaller size after shrinking the filesystem size. Maybe I have it wrong but this sounds like it would delete any data stored? I tried to use parted as well but I always seem to get "support for opening ntfs partitions is not yet implemented".

---

### Post by Cheesemill on 2012-06-26
> **Delarth said:**
> I ran across mention of using ntfsresize but the manual talks about deleting the partition and recreating with the smaller size after shrinking the filesystem size. Maybe I have it wrong but this sounds like it would delete any data stored?

It sounds like it would delete the data but it doesn't.

You use ntfsresize to shrink the filesystem, and then use parted to delete the partition and create a new one of the correct size, you just have to be very careful with the maths when creating the new partition. This is the exacted process that gparted automates with a GUI.

I was involved in a thread where we used this process to expand an NTFS partition last month if it's any help:
[http://ubuntuforums.org/showthread.php?t=1975526](http://ubuntuforums.org/showthread.php?t=1975526)

---

