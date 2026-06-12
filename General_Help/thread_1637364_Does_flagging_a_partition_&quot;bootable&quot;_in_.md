---
title: "Does flagging a partition &quot;bootable&quot; in disk tools, format the partition?"
date: 2010-12-04
forum: General Help
---

### Post by gormers on 2010-12-04
A part of my hd is ntfs (where I keep my windows and windows files). I edited it to be flagged as "bootable" in the disk tools that comes with ubuntu 10.10, and now it wont list as a file system in ubuntu (in other words I cant access it). Was this a very bad idea? 

Thanks.

---

### Post by efflandt on 2010-12-04
I have not used Disk Tools much because I do not understand it.  The last time I "thought" I was trying to mark a partition as the boot partition with it, it started endlessly churning my hard drive and I think I may have had to do a hard power down to stop it.  But nothing was damaged, so I don't know what it was trying to do.

I use gparted instead, which comes on live/install iso (CD or USB), but is not installed by default on a regular system.  You usually cannot tamper with a partition on a drive you are running from at the time anyway.  Or I can switch boot flags with sudo fdisk, but if a a different partition is set as boot, you also need to clear the boot flag from partition it was set to previously.

If you are booting from grub in the mbr, what you mark as the boot partition is totally ignored anyway.  The boot flag would only be used if you have a standard Windows mbr, so it knows which partition to boot.

For example when a flawed Win7 program (Dell DataSafe I think) stepped on grub in my mbr, I installed grub to primary Linux partition sda4 instead, restored standard Windows mbr, then marked sda4 as the boot partition (so Windows mbr would boot that).

---

### Post by gormers on 2010-12-04
Looks like it did something fun here. I downloaded gparted and aother disk manager, and they cant recognize what sort of filesystem this is anymore. I guess it got corrupted for some reason?

And yeah this was the hd I was running while using the program. I did remove the flag and I do use grub anyways, but I guess this doesnt matter anymore because there prolly isnt a way to try to fix this..? (it lists all other info than what file system it is though)

---

### Post by oldfred on 2010-12-04
Boot flag is just that a flag on the partition, but it has to rewrite the partition table if that did not work correctly you can have trouble.

I might try test disk.

enable the "universe" repository to download testdisk
System>Administration>Software Sources>Ubuntu Software.
[https://help.ubuntu.com/community/DataRecovery](https://help.ubuntu.com/community/DataRecovery)
Instructions
[http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step](http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step)
[http://www.cgsecurity.org/wiki/Menu_Analyse](http://www.cgsecurity.org/wiki/Menu_Analyse)

repairs including testdisk info & links
[http://members.iinet.net.au/~herman546/p21.html](http://members.iinet.net.au/~herman546/p21.html)
[https://help.ubuntu.com/community/DataRecovery#Lost%20Partition](https://help.ubuntu.com/community/DataRecovery#Lost%20Partition)

---

### Post by gormers on 2010-12-04
What a fantastic program! I was able to list the files in the problematic partition, and copy the most important files over. Ill see more into your useful links if Ill be able to recover the whole partition. 

Thanks for the help everyone, Im really happy now xP

---

