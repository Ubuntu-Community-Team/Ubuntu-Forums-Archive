---
title: "Recover NTFS data from ex-swap partition"
date: 2012-06-19
forum: General Help
---

### Post by DjMike681 on 2012-06-19
Hello everyone!

Yesterday I decided myself to change my OS from Windows 7 to Ubuntu  (I've been using Windows and Ubuntu on a VM for a while, so I was pretty familiar). I had to partitions, one with windows and another one with fair amount of data (~250GB). I decided that I would install Ubuntu in the place of Windows. So I did. I ran the installation. The trick was in the partition table selection. I have selected the ext2 system for ubuntu, buuut the eizard asked me to choose a swap device (because is better!?). I checked that, even though I was not sure about consequences. After the installation finished, I first checked if my data was there. It was not there in the UI, so i checked in terminal. The drive was there, but it was swap-labeled. I searched for some info on the web and I tried this [this]("http://askubuntu.com/questions/98790/how-to-recover-data-from-ntfs-partition-that-was-made-into-a-swap-partition"). I was superficial and I did not followed carefully, therefore there was no result. That's why I decided to install windows again :\. I did that and i formated the prev. installed ubuntu. Now the partition is there, [in Windows Disk Management]("http://lookpic.com/O/i2/614/XQZCilFL.png"), but it says 100% free ... . 

**My question: Is there any way I can recover the data from that partition, or I can just forget it ?**

*(Luckily I have backed up some of the most important files on google docs)*

Thanks!

---

### Post by oldfred on 2012-06-20
Not sure but stop using partition. If swap was used it may have overwritten part of it, but if you have lots of RAM it may not have been used.

You need to boot with a liveCD that does not automount swap partition and use it to speed up liveCD. Ubuntu liveCD auto mounts swap and I am not sure if swapoff is one of the boot options or if it works to try to turn it off.

[http://www.howtoforge.com/data_recovery_with_testdisk](http://www.howtoforge.com/data_recovery_with_testdisk)
They suggest gparted or Knoppix but I do not know if on booting you can swapoff or not.

From liveCD you may be able to run testdisk and recover partition.

Instructions
[http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step](http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step)
[http://www.cgsecurity.org/wiki/Menu_Analyse](http://www.cgsecurity.org/wiki/Menu_Analyse)
[http://www.cgsecurity.org/wiki/TestDisk:_undelete_file_for_NTFS](http://www.cgsecurity.org/wiki/TestDisk:_undelete_file_for_NTFS)

---

### Post by oldfred on 2012-06-20
I just booted my gparted ISO and it did not mount any swap partitions.

This is the version I used.
gparted-live-0.12.1-5.iso

[http://gparted.sourceforge.net/faq.php](http://gparted.sourceforge.net/faq.php)

---

