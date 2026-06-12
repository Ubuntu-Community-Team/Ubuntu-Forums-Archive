---
title: "Think I need help restoring MBR."
date: 2011-08-09
forum: General Help
---

### Post by UserName: on 2011-08-09
I can't boot into Windows or even Ubuntu at all.
 
I want to just have Windows 7 on my computer.

I deleted every single partition and have nothing but unallocated space on my HDD according to GParted. Right now I am running Ubuntu 10.04 LTS (Lucid Lynx) through a USB hard drive.

As far as I understand, I can install windows. I actually did it twice before deleting partitions and all... but I can't seem to boot into Windows 7 because I need to repair the MBR/GRUB...

I only have a recovery disc that came with the computer so I can't use the method that most people are recommending me, which is the one that uses an installation disc.

Basically, I need to use Ubuntu to repair my computer so that it can boot into Windows 7.

____________________________________________________________________________________

**One way I tried to do this already was...**


**1) System > Administration > Software Sources**

 Here, I check marked  "*Community maintained Open Source Software (universe)*"



[B]2) Applications > Accessories > Terminal 


[/B]
Then I typed in this command:

*sudo apt-get install ms-sys*



but then, I got this, I think this is an error:

[I][COLOR=Black]Reading package lists... Done
Building dependency tree       
Reading state information... Done
[COLOR=Red]E: Couldn't find package ms-sys
[/COLOR][/COLOR][/I][COLOR=Black][COLOR=Red][COLOR=Black]
[/COLOR][/COLOR]______________________________________________________________[/COLOR][I][COLOR=Black][COLOR=Red]

[/COLOR][/COLOR][/I][COLOR=Black][COLOR=Red][COLOR=Black]**I was trying to use this tutorial:**

[/COLOR][/COLOR][/COLOR][http://www.arsgeek.com/2008/01/15/how-to-fix-your-windows-mbr-with-an-ubuntu-livecd/](http://www.arsgeek.com/2008/01/15/how-to-fix-your-windows-mbr-with-an-ubuntu-livecd/)



Thanks for taking the time to read. It truly is appreciated.

---

### Post by Megaptera on 2011-08-09
I don't have _install_ discs but in Vista using my _recovery_ disc I've sucessfully used this method. Have you tried the recovery disc in your W7?

[http://www.lancelhoff.com/how-to-fix-vista-mbr-repair-broken-vista/](http://www.lancelhoff.com/how-to-fix-vista-mbr-repair-broken-vista/)

---

### Post by garvinrick4 on 2011-08-09
If you still have an operating system at all check by.
```
sudo fdisk -l 
```(lower case L)

#If you do have a Windows install left to boot but do not have a disk can use lilo to
boot with.
  	 	 	 	 	 	  Restore basic windows boot loader - universe enabled 
```
sudo apt-get install lilo
```
```
sudo lilo -M /dev/sda mbr
```
May show error messages about the rest of lilo missing, ignore, we just want MBR


[LEFT]#If you do not have a operating system and no disks I see no way to install Windows short of buying some disks.

[/LEFT]

---

### Post by Rushyang on 2011-08-09
I believe.. This URL will help

[http://www.howtogeek.com/howto/32523/how-to-manually-repair-windows-7-boot-loader-problems/](http://www.howtogeek.com/howto/32523/how-to-manually-repair-windows-7-boot-loader-problems/)

---

### Post by UserName: on 2011-08-09
> **garvinrick4 said:**
> If you still have an operating system at all check by.
```
sudo fdisk -l 
```(lower case L)



I feel pretty certain I don't have any operating system, but I could definitely be wrong so I did it anyways and got this.

[I]ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/sda: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x890a2267

   Device Boot      Start         End      Blocks   Id  System

Disk /dev/sdb: 1001 MB, 1001390080 bytes
255 heads, 63 sectors/track, 121 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x04dd5721

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1         122      977888+   b  W95 FAT32
Partition 1 has different physical/logical endings:
     phys=(120, 254, 63) logical=(121, 190, 5)
ubuntu@ubuntu:~$ ^C
[/I]
I honestly have no idea if this means there's an operating system or not, lol.

But... when I go to the Install Ubuntu, it checks the hard drive for partitions and how many other OS's there are and at the moment it says there are zero and the entire hard drive is free. Before I deleted the partitions, it said there was several. Here is a screenshot oh how it is now.

[IMG]http://i580.photobucket.com/albums/ss248/evilragdoll333/Screenshot-4.png[/IMG]


I can install Windows 7 because I actually do have the recovery disks, but I simply decided to not install it again before I asked you guys for help.

So do I install Windows 7?

Just trying to be cautious and not complicate things anymore since I already messed up pretty badly- lol. 

Thanks by the way, you guys are awesome.

---

### Post by westie457 on 2011-08-09
Hi looking at the picture you have completely wiped the hard drive.
There is no Windows recovery/restore partition.

A Windows recovery disc only allows you to repair a broken Windows system. You cannot install Windows with it. You need to use a restore/backup disc (1 or more DVD's) to reinstall Windows. If you have neither then to install Windows either buy a new DVD or contact your computer manufacturer and ask them for a copy of their restore discs. You will have to pay for these, maybe not as much as Microsoft charge.

---

### Post by westie457 on 2011-08-09
There is a chance that your Windows partitions can be recovered using [testdisk]("http://www.cgsecurity.org/wiki/TestDisk").

It is a slim one though. If testdisk is able to find and restore them we have a very good chance of being able to help you.

Assuming testdisk works could you then download and run bootinfoscript. Download and usage instructions are available here. [http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)

This is best run from a LiveCD.

---

