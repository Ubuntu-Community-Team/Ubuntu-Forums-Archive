---
title: "Deleting /home partition"
date: 2011-09-29
forum: General Help
---

### Post by yotamoo on 2011-09-29
Hi there
I would like to delete the partition hosting my home folder and create a new one instead. The way I understand it I need to back up my home folder and delete the partition. But what do I do after I've created a new one? How do I set home to that partition?
Is it only a matter of mounting, or should I set other variables? Thanks

---

### Post by grahammechanical on 2011-09-29
Just a reminder.

Do all of this from a Live CD. Ubuntu needs a home folder or home partition to work. Shortly after installing Ubuntu in 2007 I decided to create a home partition. I followed a guide in a computer magazine which failed to point out that I would need to re-install Ubuntu into the / partition and assign/mount the new home partition as /home - result = a broken system. Ubuntu could not find the home folder and all the settings in it! It did not know that I now had a /home partition.

Now, some on this forum may be able to advise you on how to avoid this happening to you. They will tell you what commands to run. My simple advice is to do this at a time when you want to re-install, such as when upgrading to the latest Ubuntu. Use the Do Something Else option to delete and create partitions. Set mount points for / and /home and mark for formatting. Let the install process do the work and then copy the data from the old home partition into the home folder on the new home partition. Then the programs will load with the same settings and documents as now. I have done this when I have wanted to format my /home partition to clear away conflicting configuration files from programs that I no longer use.

Regards.

---

### Post by oldfred on 2011-09-29
It is primarily the mount in fstab.

Your moving to a new partition is not really different than moving from inside / to a partition, so you should be able to follow these guides.

# MoveHome.txt
Uses cp -ax
[http://www.ivankuznetsov.com/2008/04/moving-home-to-its-own-partition.html](http://www.ivankuznetsov.com/2008/04/moving-home-to-its-own-partition.html)
cp without -a and copying as sudo root takes ownership
To move /home uses rsync  
[https://help.ubuntu.com/community/Partitioning/Home/Moving](https://help.ubuntu.com/community/Partitioning/Home/Moving)
Uses cpio
[http://www.psychocats.net/ubuntu/separatehome](http://www.psychocats.net/ubuntu/separatehome)

I have gone from separate /home to data partition(s) /mnt/data (ext3) & /mnt/share (ntfs) with links into my home for all my standard folders. I now have home inside root and it is only 1GB as I aggressively move all data folders including hidden ones like the Firefox & Thunderbird profiles.

---

### Post by dcstar on 2011-09-30
> **oldfred said:**
> 
......
I have gone from separate /home to data partition(s) /mnt/data (ext3) & /mnt/share (ntfs) with links into my home for all my standard folders. I now have home inside root and it is only 1GB as I aggressively move all data folders including hidden ones like the Firefox & Thunderbird profiles.

A separate /home means you can install/reinstall Ubuntu as many times as you like without any loss of the data and configuration settings in /home.

IMHO not having a separate /home is just crazy, and it should be in the standard Ubuntu setup as many novice users do reinstall Ubuntu unintentionally wiping all of their /home data because of this issue.

Add in all the other benefits of reducing the risk of root filesystem corruption in the event of system crashes or power failures and the case for a separate /home is basically compelling.

---

### Post by oldfred on 2011-09-30
@dcstar
I agree for most users a separate /home makes the most sense. And for new users my install suggest is always a separate /home over the default install. But more advanced users I suggest the data partitions as an alternative.

My way works for me as each install is in a new partition (or over one several versions old) so I can copy my internal /home over if I want directly from old install to new. I usually only copy some settings. Also because I have so little in my /home it is easy to backup. I have regular rsync and periodic DVD backups of /home.

---

