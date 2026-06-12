---
title: "Mounting partition on 2nd drive, drive not recognized"
date: 2012-04-19
forum: General Help
---

### Post by dsr10 on 2012-04-19
I just installed Ubuntu 11.10 desktop to a seperate drive on my system that already has windows 7 installed on the other drive. The drive with windows 7 also has a partition for data (including pics and media) that I would like to be able to access from Ubuntu as well as win7.

My Ubuntu doesn't see the other drive at all, in the past I could have sworn I was able to access drives with a Windows created data partition. How can I find and mount this partition to make it available to both operating systems?

---

### Post by 2F4U on 2012-04-19
Is the Windows partition encrypted or compressed? This seems to be a problem:

[https://help.ubuntu.com/community/MountingWindowsPartitions#Known_Issues](https://help.ubuntu.com/community/MountingWindowsPartitions#Known_Issues)

---

### Post by oldfred on 2012-04-19
Welcome to the forums.

Did you use Windows to create extra partitions and it converted you to dynamic partitions? Linux does not work with dynamic partitions only basic in Windows terminology. 

Post this 

sudo fdisk -lu

---

### Post by dsr10 on 2012-04-19
Well, it's not encrypted or compressed, that I do know. I'm pretty sure when I set this up last year that I created a dynamic partition.

Do you know if I would be able to pull that data off and go back and make that partition a basic partition? I'd prefer not to have to reinstall Windows, if at all possible.

If so, I'm wondering if I might be better off having the Ubuntu and Windows installations on the same drive, then moving my data to the second drive. The only reason I set it up this way was because I already had the other drive partioned, etc.

Thanks for the help guys, I really appreciate it.

---

### Post by oldfred on 2012-04-19
I normally suggest that each system should be on a separate drive if you have more than one drive. Then if one drive fails you can boot the other.
It also helps to separate boot loaders and keep them on the same drive as the system. Sometimes Windows gets particular when other systems are around.

Some Windows software may convert back. Windows official policy is to backup, delete everything and create new basic partitions. Easeus's free version was able to do converson. I think you have to pay for Mini-Tool version that works for conversion.

Converted with EASEUS Partition Master
[http://ubuntuforums.org/showthread.php?t=1692248](http://ubuntuforums.org/showthread.php?t=1692248)
[http://www.partition-tool.com/personal.htm](http://www.partition-tool.com/personal.htm)

Dynamic volume is a Microsoft proprietary format developed together with Veritas (now acquired by Symantec) for logical volumes.
You may be use a third-party tool, such as Partition Wizard MiniTool or EASEUS to convert a convert a dynamic disk to a basic disk without having to delete or format them.
The Partition Wizard software for Windows is supposed to be able to convert dynamic disks to regular partitions without data loss, so it may be what you need to get around this problem; however, I've never used it and so I can't be sure it will work.

---

### Post by dsr10 on 2012-04-22
Thanks for the info everyone. I've got it all working properly now, guess I'll see if I can figure out how to mark this thread solved.

Thanks again.

---

