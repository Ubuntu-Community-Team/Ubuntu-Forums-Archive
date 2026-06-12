---
title: "Ubuntu doesn't detect all my partitions"
date: 2009-06-26
forum: General Help
---

### Post by Jordanwb on 2009-06-26
I wanted to reinstall Ubuntu after reinstalling Windows XP. I attempted to make a backup of my Ubuntu install but the system crashed leaving me with a corrupted tar file (I had assumed the backup had completed). I have three hard drives: one 320GB (sda), and two 160GB (sdb & sdc). The latter two are part of a Windows XP software RAID. The first drive is a "dynamic" drive (whatever that means). The first partition is 160GB containing XP. I booted 9.04 amd64 and used gparted to make some additional partitions. For some reason I reboot my computer (Ubuntu not installed) and XP won't boot. I get the XP logo and then it BSOD's. I delete the non-Windows partitions and XP boots fine. 

I use XP's Disk Management program to make the partitions but neither fdisk or gparted detect them. They detect the XP partition just fine. What do I do?

[Edit] Apparently the "dynamic" disk's partition table isn't GPT has I had thought.

---

