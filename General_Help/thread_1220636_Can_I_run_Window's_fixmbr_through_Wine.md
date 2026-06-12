---
title: "Can I run Window's fixmbr through Wine?"
date: 2009-07-23
forum: General Help
---

### Post by AcousticMinja on 2009-07-23
I attempted to dual boot Vista with Kubuntu (with Vista installed first and on my first hard drive and Kubuntu on my second hard drive.)
When I started up after restarting my computer, I got grub error 22. I decided to uninstall Kubuntu using the liveCD and gparted.
Here's my problem now, I get grub 1.5 error 17 when trying to start up.
I have absolutely no blank CDs whatsoever and my CD burner on my computer is not working properly with Ubuntu. 
I booted up with my liveCD and am using ubuntu 9.04 right now.
I've tried doing everything people have told me, but it requires burning an iso to a disc.

So, I successfully installed wine and I am wondering if I could possibly download, run, and properly use fixmbr. I don't really have any other way of getting in to Vista and I have to use this computer for my daily tasks. I do love Ubuntu and would plan on installing it again, but I need to get Vista working first. I can't afford to lose any of my data right now either so please, someone let me know if I can use fixmbr through wine, or somehow use a USB stick to boot from, or anything else WITHOUT a blank CD.
:(

---

### Post by BenAshton24 on 2009-07-23
I doubt that that would be work...

an easier way would be to download SuperGrub: [http://supergrub.forjamari.linex.org/](http://supergrub.forjamari.linex.org/)

Burn it to a cd or stick it on a pen drive... then boot into it like a regular live CD and it will give you options and should allow you to restore your mbr

Hope this helps, 
Ben :D

---

### Post by lisati on 2009-07-23
If you have a Windows recovery or installation disk, or a recovery partition you can boot from, you *might* be able to run fixmbr from there. 

If all you have is a recovery partition, it might be a good idea to look into making a backup a.s.a.p. - some computers come with software that will do the job for you preinstalled.

---

### Post by Zorael on 2009-07-23
I'm not sure I understand. You just want to restore a vanilla MBR to the drive, to make it start the partition flagged as active/boot instead of grub? I know for sure **testdisk** in the universe repo can do this.

Run it (in a terminal, with sudo), pick your drive, choose Intel partition table, and then MBR Code.
```
TestDisk 6.10, Data Recovery Utility, July 2008
Christophe GRENIER <grenier@cgsecurity.org>
http://www.cgsecurity.org


Disk /dev/sda - 80 GB / 74 GiB - CHS 9729 255 63

[ Analyse  ]  Analyse current partition structure and search for lost partitions
[ Advanced ]  Filesystem Utils
[ Geometry ]  Change disk geometry
[ Options  ]  Modify options
**[ MBR Code ]  Write TestDisk MBR code to first sector**
[ Delete   ]  Delete all data in the partition table
[ Quit     ]  Return to disk selection






Note: Correct disk geometry is required for a successful recovery. 'Analyse'
process may give some warnings if it thinks the logical geometry is mismatched.
```
You should be able to set the active/boot flag under Advanced, too. (or in fdisk)

---

