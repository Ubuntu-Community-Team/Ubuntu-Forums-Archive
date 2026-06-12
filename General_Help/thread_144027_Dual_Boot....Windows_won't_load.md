---
title: "Dual Boot....Windows won't load"
date: 2006-03-13
forum: General Help
---

### Post by hickoryknot on 2006-03-13
Hi all...I have been using a dual-boot setup for several months now without any problems..Today when I tried to boot Windows I got this:

Booting "Microsoft Windows XP Home Edition"
root  (hd0,1)
Filesystem type unknown partition type 0x7
savedefault
makeactive
chainloader +1

I have tried shutting down and rebooting several times with no luck......I would sure appreciate it if someone could help...
Thanks....

---

### Post by Zelut on 2006-03-13
Well I haven't ever seen this before but I have a few ideas of things to look at.

In my experience (anyone jump in if I'm wrong) Microsoft makes itself the first item on the MBR.  On my system anyway my listing for XP is "root (hd0,0)".  I wonder if somehow your /boot/grub/menu.list was changed.  Maybe check that file & see if its conflicting with another entry.. maybe it tries to load XP and then finds a non-XP partition??

Thats my best first guess on what to check.

---

### Post by lha on 2006-03-13
Do
```
sudo fdisk -l
```
and post output here.

---

### Post by hickoryknot on 2006-03-13
Disk /dev/hda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1               1           4       32098+  de  Dell Utility
/dev/hda2   *           5       30147   242123616    7  HPFS/NTFS
Partition 2 does not end on cylinder boundary.
/dev/hda3           30147       30386     1919736   83  Linux
Partition 3 does not end on cylinder boundary.
/dev/hda4           30386       30401      120487+   5  Extended
Partition 4 does not end on cylinder boundary.
/dev/hda5           30386       30401      120456   82  Linux swap / Solaris

Disk /dev/hdb: 200.0 GB, 200049647616 bytes
255 heads, 63 sectors/track, 24321 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdb1   *           1       12158    97659103+  83  Linux
/dev/hdb2           24087       24321     1887637+   5  Extended
/dev/hdb5           24087       24321     1887606   82  Linux swap / Solaris

---

### Post by lha on 2006-03-14
Replace
```
root (hd0,1)
``` with
```
rootnoverify (hd0,1)
``` in menu.lst. (Open terminal and type
```
cd /boot/grub
sudo cp menu.lst menu.lst_backup
sudo gedit menu.lst
```.) I have seen that 'Filesystem type unknown partition type 0x7' error before and replacing root with rootnoverify helped.

---

### Post by hickoryknot on 2006-03-14
I tried this and when I attempt to boot into windows this is what shows...

rootnoverify    (hd0,1)
savedefault
makeactive
chainloader +1

---

### Post by hickoryknot on 2006-03-16
Does anyone have any more ideas on what I can do?  I am to the point now that I'm using Linux 95% of the time but there are still some things in Windows that I need......I would sure appreciate the help...
Thanks...

---

### Post by hickoryknot on 2006-03-16
It appears that Linux is unable to recognize the windows files now....I have another drive that I plug in a USB port which has a bunch of windows files on it....pics..etc.......and it won't read that drive either... It did before...Is there a way to enable this again?

---

### Post by zXen on 2006-03-16
Go into the repair facility frrom the WinXP CD and type FIXMBR, then once you have done that type HELP and type the command to fix the BOOT (I forget the exact name). This could possibly fix your boot problems.

---

### Post by lha on 2006-03-16
[QUOTE=hickoryknot]It appears that Linux is unable to recognize the windows files now....I have another drive that I plug in a USB port which has a bunch of windows files on it....pics..etc.......and it won't read that drive either... It did before...Is there a way to enable this again?[/QUOTE]

I can't help you with that.

If you do tell Windows cd to overwrite your mbr ("remove grub"), you should get Windows back. Then [reinstall grub]("http://ubuntuforums.org/showthread.php?t=76652") on linux partitions (hda3) boot sector and use [BootPart]("http://www.winimage.com/bootpart.htm") to get NTLDR able to load grub.

Those 'Partition X does not end on cylinder boundary.' give me the creeps, but I don't know if your problem lies there... What program did you use to partition your drive?

---

### Post by hickoryknot on 2006-03-16
I used the one that was on the Ubuntu 5.10 install CD.....

---

### Post by lwatcdr on 2006-03-16
I have EXACTLY the same problem after installing Ubuntu 5.10. I am using a 200 gig SATA drive and get the exact same error.
Here is my fdisk -l

Disk /dev/sda: 203.9 GB, 203928109056 bytes
255 heads, 63 sectors/track, 24792 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       12455   100044756    7  HPFS/NTFS
/dev/sda2           12456       12467       96390   83  Linux
/dev/sda3           12468       12722     2048287+  82  Linux swap / Solaris
/dev/sda4           12723       24792    96952275   83  Linux


This is what it says in my menu.lst file
# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Windows XP Media Center Edition
root		(hd0,0)
savedefault
makeactive
chainloader	+1

And this is my device.map file
(hd0)	/dev/sda

I am using ubuntu AMD64 5.10
Any suggestions about what is wrong would be great.

---

### Post by lha on 2006-03-17
[QUOTE=lwatcdr]I have EXACTLY the same problem after installing Ubuntu 5.10. I am using a 200 gig SATA drive and get the exact same error.
Here is my fdisk -l
[B].
.
.[/B]
This is what it says in my menu.lst file
# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Windows XP Media Center Edition
root		(hd0,0)
savedefault
makeactive
chainloader	+1

And this is my device.map file
(hd0)	/dev/sda

I am using ubuntu AMD64 5.10
Any suggestions about what is wrong would be great.[/QUOTE]

Your menu.lst looks good to me. Maybe you should try the method I described in my previous post to this thread.

---

