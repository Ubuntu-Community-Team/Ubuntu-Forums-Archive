---
title: "File System Damaged!Helpppp"
date: 2010-01-20
forum: General Help
---

### Post by ssj6akshat on 2010-01-20
GRUB says my filesystem is damaged and it gives me a "grub rescue>" prompt.Please Help Me.I am not a noob but i am no geek either.

---

### Post by ssj6akshat on 2010-01-20
Please Help Me it had very important files of my Father

---

### Post by x33a on 2010-01-20
well load the livecd and run fsck on the root partition.

also, while you are at it, use the livecd to backup the important files, so that nothing is lost.

---

### Post by ssj6akshat on 2010-01-20
I am using the live CD and the disk is not appearing.Palimpest says my disk is Unused/Unallocated and GParted goes Mad

---

### Post by x33a on 2010-01-20
Hmm.. then it might be in a bad shape.

You can try testdisk.

[http://www.cgsecurity.org/wiki/TestDisk](http://www.cgsecurity.org/wiki/TestDisk)

it is available with a host of live cds:

[http://www.cgsecurity.org/wiki/TestDisk_Livecd](http://www.cgsecurity.org/wiki/TestDisk_Livecd)

---

### Post by robert.mcnutty on 2010-04-10
I had the same issue using Ubuntu 9.10. Palimpest was reporting drive was going bad. I had seen numberous posts about false errors with Palimpest. I ran every switch combination of FSCHK and tried different utilities. All reported that there were no issues. Eventually Palimpest caused the disk to fail by copying sectors and ultimately flagging the partitioned as failed. Every time I have used a Linux distro that used Palimpest, Palimpest reports drive errors. Even when I run the distro as vm on ESXi. Therefore I refuse to use any distro which uses Palimpest. 

To fix this problem, I used Parted Magic live thumbdrive to get a live session and recover data. Using Ubuntu 9.04 live cd did not work. Parted Magic was able to present the internal HDD and partitions. Once it was up, plugged in another USB thumb drive to copy the files. Once I was done backing up the files, I used the DD utulity in Parted Magic to "zero out" the whole drive. Once completed, I rebooted the pc with an Ubuntu 9.04 live cd to reinstall. Since then I have had no problems with the disk. I still won't use Palimpest either. I'm very disappointed with Ubuntu for switching to this awful utility. 

Good luck!!

---

