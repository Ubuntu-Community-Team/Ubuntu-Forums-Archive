---
title: "Grub packaged with Karmic works, but Grub with Jaunty doesn't??"
date: 2009-11-15
forum: General Help
---

### Post by ThinkEntropy on 2009-11-15
I installed Jaunty along with XP recently, and everything worked great /except/ the dual boot functionality.  It would boot into Ubuntu fine, but when I selected XP, I'd get a Windows Boost Loader error saying: 

"0xc000000e -- The boot selection failed because a required device is inaccessible."  

My only option is to reboot at this point.  I thought this was a silly Windoze issue since it made it into the boot loader...

Then I upgraded to Karmic, and the dual boot function worked!!!  I was so happy!  Unfortunately, my systems locks up randomly using Karmic, so I had to go back to Jaunty.  DOH! :(

But here I am back to square one, and I can't figure out what I'm doing wrong.  I figure something with Grub is fishy, since simply installing 9.10 with no other changes to the Windows drive fixed the issue.  But I have no idea where to start.  Can anyone maybe provide some guidance?

fstab -l output:

```
Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xab0ff406

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       59343   476672616   83  Linux
/dev/sda2           59344       60801    11711385    5  Extended
/dev/sda5           59344       60801    11711353+  82  Linux swap / Solaris

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x8b8e9151

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1       60801   488384001   83  Linux

Disk /dev/sdc: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xf1968eba

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   *           1      121601   976760001    7  HPFS/NTFS

Disk /dev/sdd: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xf4e2181f

   Device Boot      Start         End      Blocks   Id  System
/dev/sdd1   *           1        9728    78140128+   7  HPFS/NTFS

```If it helps, here is the part of my menu.lst file pertaining to Windows (/dev/sdd is where XP is installed):

```
title        Microsoft Windows XP Professional
 rootnoverify    (hd3,0)
 savedefault
 makeactive
 map        (hd0) (hd3)
 map        (hd3) (hd0)
 chainloader    +1
```Oh, and I also tried upgrading to Grub2 since from what I understand that's what comes packaged with Karmic, but it basically yielded the same result (maybe not surprisingly).

---

### Post by dcstar on 2009-11-15
> **ThinkEntropy said:**
> I installed Jaunty along with XP recently, and everything worked great /except/ the dual boot functionality.  It would boot into Ubuntu fine, but when I selected XP, I'd get a Windows Boot Loader error saying: 
.........
If it helps, here is the part of my menu.lst file pertaining to Windows (/dev/sdd is where XP is installed):

```
title        Microsoft Windows XP Professional
 rootnoverify    (hd3,0)
 savedefault
 makeactive
 map        (hd0) (hd3)
 map        (hd3) (hd0)
 chainloader    +1
```Oh, and I also tried upgrading to Grub2 since from what I understand that's what comes packaged with Karmic, but it basically yielded the same result (maybe not surprisingly).

Installing the new Ubuntu system in a new partition has changed the order of your partitions, which is probably what Windows is complaining about.

Grub2 automatically detects all O/S on your machine and sets up the launch strings automatically, whereas in Grub you have to make these changes manually if you do things like adding partitions. The "(hd3)" is probably wrong now.

Installing other versions of the Grub packages does not necessarily configure your system to actually use them:

[http://www.howtoforge.com/how-to-install-grub-2-on-ubuntu-9.04](http://www.howtoforge.com/how-to-install-grub-2-on-ubuntu-9.04)

---

### Post by ThinkEntropy on 2009-11-15
David, thank you so much for your help!  Please bear with me as I am new to Ubuntu, so if you don't mind please let me see if I'm understanding you correctly.

You believe my pointing Grub to (hd3) is the problem.  I installed XP on (what I believe to be) sdd1, so I thought pointing Grub to (h3,0) would do the trick.  Is that not correct?  If Windows is installed on sdd1 what *should* I be entering in the menu.lst file?

Thanks for pointing a newb in the right direction sir ;)

---

### Post by ThinkEntropy on 2009-11-16
bump

---

### Post by ThinkEntropy on 2009-11-17
bump

---

### Post by ThinkEntropy on 2009-11-19
bump :(

---

