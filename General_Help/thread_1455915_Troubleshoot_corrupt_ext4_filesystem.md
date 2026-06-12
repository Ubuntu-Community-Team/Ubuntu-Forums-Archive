---
title: "Troubleshoot corrupt ext4 filesystem"
date: 2010-04-16
forum: General Help
---

### Post by Bill Day on 2010-04-16
For the second time, I am having issues with a corrupted ext4 filesystem.  My machine has run flawlessly for weeks, then all of a sudden I am getting messages that I can't access various directories, and on reboot fsck dumps to a command line.  So far I have been able to fix the problem by manually running fsck.  However, this is the second time that I have run into this problem; the previous time I ended up throwing out my hard drive and doing a clean install.

I am running a clean install of Karmic Koala, software RAID, 4 Gb RAM, two 500 Gb Western Digital SATA drives, with an Intel E7200 2.53 Ghz dual core processor.

Among other applications, I run VMware 7.0 for the occasional task for which I need a Windows program.

I am hoping for suggestions of a specific series of diagnostic tests I could run to try to troubleshoot this problem.  Thanks.

---

### Post by PeterBBB on 2010-04-17
I don't run ext4, but I would suggest installing smartmontools to see if you have a hardware problem with the drive. Also try changing the fsck frequency to check more often.

[http://ubuntuforums.org/showthread.php?t=300477](http://ubuntuforums.org/showthread.php?t=300477)

---

