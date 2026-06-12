---
title: "How can I access my windows folders with Ubuntu Live"
date: 2011-04-06
forum: General Help
---

### Post by Tarnie on 2011-04-06
Hello everybody. Two days ago my Windows 7 just crashed and it doesn't work any more. Using a computer in a Internet point a downloaded Ubuntu 10.10 Live and now I'm running it in my computer. I would like to install Ubuntu definitely on my computer but before I would like to find all my old file from Windows 7. 
In Places/Computer has only the File System and nothing else. In System/Administration/Disk Utility I can see my 320 GB hard Disk (ATA Samsung HM3200II) but I can't do anything in that. 
I tried to use the Ubuntu 10.10 live in other computer and this work perfectly, but in this one no. What can I do to right now?

---

### Post by TeoBigusGeekus on 2011-04-06
Go to applications>accessories>terminal
Post us the output of
```
sudo fdisk -l
```
that's the letter not the number(1)

---

### Post by Tarnie on 2011-04-06
i did that and nothing change:
The terminal says that:

Disk /dev/sdb: 4009 MB, 4009754624 bytes
145 heads, 48 sectors/track, 1125 cylinders
Units = cylinders of 6960 * 512 = 3563520 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xc3072e18

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1        1126     3915752    c  W95 FAT32 (LBA)

---

