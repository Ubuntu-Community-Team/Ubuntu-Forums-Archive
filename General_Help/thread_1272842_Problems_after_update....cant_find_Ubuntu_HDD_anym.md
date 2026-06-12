---
title: "Problems after update....cant find Ubuntu HDD anymore"
date: 2009-09-22
forum: General Help
---

### Post by Thonyv on 2009-09-22
This morning Update Manager popped up with 3 updates. Can't recall what exactly they were but they were security updates so I installed them. Shortly there after I tried to run Zuma with Wine and everything started going crazy. I got a weird error message about "Missing Resources" with a bunch of unreadable characters and then my whole desktop froze except for the mouse. Couldn't do anything so I hit the reset button.

After that, I have not been able to boot back into my Ubuntu OS and the Live CD does not even see the HDD or partitions on it. It does however see the 2 windows partitions on my other HDD. I can still get the Grub list when I boot and it shows all the Linux kernels from 2.6.28-11 to 2.6.28-15 as well as my Windows OS (different HDD). I can boot into Windows but I get error messages when I try to load any of the linux kernels. Says something like cylinders are to large....sorry cant recall exactly until I reboot and try it again.

Everything has been fine for months, installed this OS when 9.04 went live. I have been searching the forums all day trying to find a solution and all the threads that seem close to my problem haven't worked because it cant see my HDD. The BIOS does detect it though and it is set as my primary HDD.

Any help is much appreciated....sorry if my info is lacking I am still pretty new to linux.

---

### Post by egalvan on 2009-09-22
Boot with a LiveCD and run Partition Editor (gparted).
See if it can find the drive.
If so, post a screen-shot.

next, run

```
sudo blkid
sudo fdisk -l
```

and post the results.

---

### Post by Thonyv on 2009-09-22
Thanks, tried that earlier and Gparted could not find the Linux partitions either. Ran the blkid and fdisk -l anyway and only got info on the 2 windows partitions on the other HDD.

ubuntu@ubuntu:~$ sudo blkid
/dev/loop0: TYPE="squashfs" 
/dev/sda1: UUID="2050705050702F22" TYPE="ntfs" 
/dev/sda5: UUID="3A909F23909EE523" TYPE="ntfs" 
ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/sda: 200.0 GB, 200049647616 bytes
255 heads, 63 sectors/track, 24321 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x88438843

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       12748   102398278+   7  HPFS/NTFS
/dev/sda2           12749       24320    92952090    f  W95 Ext'd (LBA)
/dev/sda5           12749       24320    92952058+   7  HPFS/NTFS

---

### Post by Thonyv on 2009-09-22
Ok just restarted and looked at some of the info in the Grub menu. It has to be somewhere because Grub can still read it. I get the following when I edit the latest kernel

uuid 6cda1da7-869d-49-b3-9dbd-a74fc9448a3d

kernel /boot/vmlinuz-2.6.28-15 generic root=UUID=6cda1da7-869d-49-b3-9dbd-a74fc9448a3d ro quiet splash

inird /boot/initrd.img-2.6.28-15-generic

quiet

After I try to boot to this kernel

Boot from (hd1,0) ext3 6cda1da7-869d-49-b3-9dbd-a74fc9448a3d

Error 18: Selected cylinders exceed maximum supported by BIOS

Press any key to continue....

I read something earlier about someone mounting a hdd that gparted couldnt detect....going to see if I can find it again now that I found this info on the hdd

---

### Post by Thonyv on 2009-09-22
Well the only thing I did different this time was to edit the kernel info at the Grub menu (didn't actually change anything), but now Ubuntu can detect my Linux partition.

I still get the Error 18 when I try to boot to it and that has never happened before today

```
ubuntu@ubuntu:~$ sudo blkid
/dev/loop0: TYPE="squashfs" 
/dev/sda1: UUID="2050705050702F22" TYPE="ntfs" 
/dev/sda5: UUID="3A909F23909EE523" TYPE="ntfs" 
/dev/sdb1: UUID="6cda1da7-869d-49b3-9dbd-a74fc9448a3d" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sdb5: UUID="d5635dbc-fb4a-42de-a135-a75212b9f824" TYPE="swap" 
ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/sda: 200.0 GB, 200049647616 bytes
255 heads, 63 sectors/track, 24321 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x88438843

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       12748   102398278+   7  HPFS/NTFS
/dev/sda2           12749       24320    92952090    f  W95 Ext'd (LBA)
/dev/sda5           12749       24320    92952058+   7  HPFS/NTFS

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x0001ef24

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       60059   482423886   83  Linux
/dev/sdb2           60060       60801     5960115    5  Extended
/dev/sdb5           60060       60801     5960083+  82  Linux swap / Solaris

```

All my data seems to be there still....guess I will try to restart one more time and see what I get lol.

---

### Post by louieb on 2009-09-22
Sounds like hardware. If your lucky its a loose cable or power connection - did you check?  Its not good when fdisk does not see the drive.  

 On the [PartedMagicCD]("http://partedmagic.com/wiki/PartedMagic.php?n=Main.PartedMagic") there is a program Gsmartcontrol that can read your hard drives on board diagnostics. Modern have self tests built in Gsmartcontrol can run them and give the results. 

[http://gsmartcontrol.berlios.de/home/index.php/en/Screenshots](http://gsmartcontrol.berlios.de/home/index.php/en/Screenshots)

---

### Post by Thonyv on 2009-09-22
Well that was the weirdest problem I have ever seen. Looks like everything is back to normal...Ubuntu booted up just fine this time and it all looks good. I guess accessing that info in the Grub menu gave it the kick start it needed.

Thanks again.

---

