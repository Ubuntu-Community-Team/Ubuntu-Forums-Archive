---
title: "Have been using Ubuntu for 6 months some questions"
date: 2012-01-14
forum: General Help
---

### Post by biosol on 2012-01-14
I've been running Ubuntu-64 first 11.04 and now 11.10 on my Sony laptop at work (I work for a large tech security company).  The experience has been good overall except for a few things.

1. It might be a physical drive issue, but more and more frequently the system is slow to shut down or when starting finds filesystem errors.  At first I always fixed them, but found that could take some time.  Recently, when I don't have time, I have ignored them at boot.  I tried running a badsector command but after a real long time it didn't seem to ever finish.  When I select the f for fix errors it eventually does, but then maybe the next week we do it over again.  (The Windows 7 partition has never incurred any filesystem/disk issues).  It's 500GB, 100GB for Ubuntu, the rest for Windows.

Any suggestion on how to really fix this?

2.  Installed 11.04 initially, then 11.10 twice.  Notice I seem to have 3 swap partitions.  How can I tell which one is in use by the current installation and how can I delete the others?

3.  gedit has lost it's menu bar (open, save, etc.) after some updates.  One time it came back after an update.  How can I fix this?

Any suggestions much appreciated.

---

### Post by howefield on 2012-01-14
> **biosol said:**
> Installed 11.04 initially, then 11.10 twice.  Notice I seem to have 3 swap partitions.  How can I tell which one is in use by the current installation and how can I delete the others?

All the swap partitions are likely being used, delete any two and Ubuntu will use the remaining one. You could use gparted (it is  on the Live CD or install via Software Centre) to delete the extra swap partitions. Remember to unmount the partitions you want to delete.

> gedit has lost it's menu bar (open, save, etc.) after some updates.  One time it came back after an update.  How can I fix this?

Go to the top panel where you'll find the gedit menu (when you have it open and it has the focus) and select View > Toolbar.

---

### Post by biosol on 2012-01-14
Following the post above, I used a gparted live CD to delete 2 of the 3 swap partitions and now receive this error on boot:

error: no such partition.
grub rescue> _

Please advise how to recover the boot/grub

---

### Post by biosol on 2012-01-14
bump, would like to fix soon.  any advice appreciated.

---

### Post by duke.tim on 2012-01-14
Hmm This is only a guess but I believe that one of the partitions you deleted was a Microsoft reserved partition, Or it could be you deleted your Ubuntu partition. Either way Grub the linux bootloader is missing some config files.

Tutorial on Bootloader repair:
[http://ubuntuforums.org/showthread.php?t=1014708](http://ubuntuforums.org/showthread.php?t=1014708)

Microsoft's answer:
[http://answers.microsoft.com/en-us/windows/forum/windows_7-system/error-no-such-partition-grub-rescue/0281b1f7-4e54-4677-bf70-2e83f81d499b](http://answers.microsoft.com/en-us/windows/forum/windows_7-system/error-no-such-partition-grub-rescue/0281b1f7-4e54-4677-bf70-2e83f81d499b)

Someone with similar problem:
[http://ubuntuforums.org/showthread.php?t=1359802](http://ubuntuforums.org/showthread.php?t=1359802)

---

### Post by biosol on 2012-01-14
Device Boot      Start         End      Blocks   Id  System
/dev/sda1            2048    28155903    14076928   27  Hidden NTFS WinRE
/dev/sda2   *    28155904    28360703      102400    7  HPFS/NTFS/exFAT
/dev/sda3        28360704   162578431    67108864    7  HPFS/NTFS/exFAT
/dev/sda4       162580478   976771071   407095297    f  W95 Ext'd (LBA)
/dev/sda5       162580480   784179246   310799383+   7  HPFS/NTFS/exFAT
/dev/sda6       960038912   976771071     8366080   82  Linux swap / Solaris
/dev/sda7       784181248   960036863    87927808   83  Linux

Partition table entries are not in disk order

---

### Post by biosol on 2012-01-14
Real sorry to double post,but wanted to be sure the system was ready for work Monday morning.

Fixed in this thread - [http://ubuntuforums.org/showthread.php?t=1909154](http://ubuntuforums.org/showthread.php?t=1909154)

---

