---
title: "Trouble Installing Grub"
date: 2006-05-19
forum: General Help
---

### Post by Gannin on 2006-05-19
Let me start with some background.  My friend came to me and asked that I reinstall Windows on his computer.  He has two hard drives, so I thought this a perfect opportunity to introduce him to Linux.

I told him I would install Windows on the first hard drive, and Linux on the second, and it would give him a menu every time he booted so he could choose which one he wanted to use.  He agreed and was looking forward to trying Linux.

His Windows drive is, I believe, an SATA drive, whereas his second drive is an IDE.  The installation of Windows went smoothly enough, though it took forever.  The installation of Ubuntu also went well.

During the installation, it said that it detected Windows on another drive, and asked if I'd like to install GRUB in the MBR.  I told it yes.  The installation finished and I rebooted.

When I rebooted, Windows came up automatically.  No GRUB menu, nothing.  I reinstalled Ubuntu in expert mode, and this time chose Lilo.  When I rebooted, it was the same thing.  Windows booted automatically with no Lilo menu.

He still expressed interest in trying Linux despite this, so I told him when the new version of Ubuntu is released, we'll try again, and if that doesn't work, we can try Mandriva.

I no longer have physical access to his computer, as he took it home with him, but considering we're going to give this another go sometime in the future, I'd like to figure out what the problem is so I can get Ubuntu up and running on his computer and introduce him to the wonderful world of Linux.  Any ideas?

---

### Post by rcarring on 2006-05-19
Is the second drive partitioned into primary and extended partitions?

Same question for the Sata drive.

XP will see C:\ as the first bootable partition, you can have an extended partition on the sata drive, with many logical drives.

XP will see D:\as the first primary partition on the ide drive, you can have an extended partition on the ide drive, with many logical drives.

Check if the primary partition on the ide drive is marked active.

(I am waiting for a drive so huge that people will run out of drive letters)

---

### Post by Gannin on 2006-05-19
The Windows drive is just one large primary partition.  The Linux drive has a primary partition and an extended partition.  The primary partition is for / (root) and the extended partition holds the swap partition.

I'm not really sure why Windows seeing a drive as active or not would affect whether or not the GRUB or Lilo menus come up at boot.

---

### Post by rcarring on 2006-05-19
It's not that Windows has to see it, but whether Grub sees it as active.

If a partition is primary but not active it won't be seen as bootable, although it's a long time since I delved into the mysteries of multiple booting partitions.

---

### Post by Gannin on 2006-05-19
Does the same thing apply to Lilo?  That a partition must be marked as active?

I did go into the Windows control panel (in which I hadn't been for a very long time) and in the administration settings, it did list both drives and detailed their partition information, and while I'm not sure about the individual partitions themselves, the Linux drive was listed as being active.

---

### Post by rcarring on 2006-05-19
Lilo has to be installed on the mbr, installing it to the Linux parttion won't work.

Lilo can only boot partitions written into the lilo.conf file (again, my knowledge is rusty as I last used lilo in 1998  )

---

### Post by confused57 on 2006-05-19
See if there is anything in this thread that may help:

[http://www.ubuntuforums.org/showthread.php?t=172264](http://www.ubuntuforums.org/showthread.php?t=172264)

---

### Post by Gannin on 2006-05-19
> 
During the installation, it said that it detected Windows on another drive, and asked if I'd like to install GRUB in the MBR. I told it yes. The installation finished and I rebooted.


I did install both GRUB and Lilo into the MBR, but it didn't work.

> 
See if there is anything in this thread that may help:

[http://www.ubuntuforums.org/showthread.php?t=172264](http://www.ubuntuforums.org/showthread.php?t=172264)


That thread had a link to yet another thread which had some information that could be very helpful indeed.

> 
1. Set BIOS to boot from SATA
2. Install XP on SATA
3. Boot from Ubuntu install CD, follow directions and at partition menu, use "guided partitioning" on the IDE drive (hda) or use "manual" to control more closely how the partitions are done
4. At the boot loader menu, do *NOT* take the default. Instead instruct the installer to put grub on the Master Boot Record of the IDE drive (/dev/hda) - *NOT* on the SATA drive (sda)
5. Ubuntu will finish phase one of install and ask you to reboot. *Immediately* enter BIOS setup and change sequence to boot from IDE drive. Let Ubuntu finish installation. If you do not yet have your network connection set up, be sure to tell installer to get packages from CD only
6. In Ubuntu go to Applications/System Tools/Terminal. You will need to open a text editor and change the grub menu file:
$cd /boot/grub
$sudo gedit menu.lst
now look for an entry (near the end) that reads like something like this:

title Microsoft Windows XP Professional
root (hd1,0)
savedefault
chainloader +1

and change it to this:

title Microsoft Windows XP Professional
root (hd1,0)
map (hd1,hd0)
map (hd0,hd1)
chainloader +1

7. save the file
8. reboot and test boot into XP


I'll have to give this a try.  Thank you.

---

### Post by rcarring on 2006-05-19
I stand corrected. I didn't realize that the sata drive worked that much differently to an ide drive. Hope it all works.

---

