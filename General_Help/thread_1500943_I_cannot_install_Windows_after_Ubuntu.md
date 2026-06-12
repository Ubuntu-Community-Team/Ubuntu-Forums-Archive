---
title: "I cannot install Windows after Ubuntu"
date: 2010-06-03
forum: General Help
---

### Post by enverhoxha on 2010-06-03
I decided to setup Windows XP on a small partition, on a laptop with Ubuntu 10.04 already installed on the whole hard disc. So I created a 12 GB unallocated space, using Gparted to shrink and move the Ubuntu partition. The unallocated space (from 0 to 12000 MiB) was then turned into an unformatted primary partition. 
Now I supposed that it should be very simple to just boot from the Windows CD and install Windows on this partition and then have a dual-boot system. Instead, when I get to press ENTER to begin installing Windows, I get this response: Windows Setup COULD NOT FIND ANY HARD DISC on your system and the installation process will be cancelled. 
I had read that in fact Windows should be installed first, but Ubuntu was already there so I didn't want to lose all the data by erasing it.
I wonder what is the solution. How come that Windows Setup doesn't see the hard disc, although the setup files are previously copied on the very same hard disc? 
Can I still install Windows after Ubuntu, or should I give up and try to recuperate the partition and to merge it again with the Ubuntu partition?
(Why do I need Windows: the games... I cannot make them work in VirtualBox.)

---

### Post by marshmallow1304 on 2010-06-03
Is your hard drive SATA by any chance?  My copy of XP was unable to detect a SATA drive.  I think there's a way to load SATA drivers into the installer, but it might be easier to check in the BIOS for an option to make the SATA drive appear as a PATA drive.

---

### Post by enverhoxha on 2010-06-03
2 years ago I installed XP on the same laptop, with no problems. I had just bought it. But it was no dual-boot, no Ubuntu. Just Windows.

---

### Post by enverhoxha on 2010-06-03
On second thought, I begin to remember that actually Windows XP should be installed by previously disabling the native SATA option in BIOS. In the past I probably re-enabled it afterward. I will try this, you were probably right.

---

### Post by asqn34 on 2010-06-03
**format** xp partition in ntfs using live cd and gparted then install xp.
Infortunately, windows will erase grub, so grab the live cd and reinstal grub. Then make an entry in grub for xp to get your dual boot.

---

### Post by Vaphell on 2010-06-03
yup, looks like the problem with sata
next time install xp first, then ubuntu - it will be a breeze.

---

### Post by wilee-nilee on 2010-06-03
> **Vaphell said:**
> yup, looks like the problem with sata
next time install xp first, then ubuntu - it will be a breeze.

The XP install to a sata drive will only work with sata drivers added during the install. It doesn't matter which order you install in if you install correctly and then just reload the mbr.

---

### Post by enverhoxha on 2010-06-06
Now I somehow succeded and I have WinXP (1st partition)  and Ubuntu (2nd partition). And Grub seems to work, when I turn on the laptop I get a menu to choose from. 
But: the menu is huge because it contains a crowd of Ubuntus (Linux 2.6.32-22, 2.6.31, 2.6.24 etc., virtual, recovery etc.etc.) And Windows comes last. The first Ubuntu (Linux 2.6.32-22-generic) is the default, so when I need Windows I have to scroll all this long list and it is a little uncomfortable. At first I even failed to notice that Windows actually was there, deep down at the end of the queue...
Are all the other Linuxes in the list necessary? Can they be eliminated to make the list shorter? 
Or maybe is there a way to change the place of Windows in this menu and bring it close to the first Ubuntu? 
Probably this means editing grub.cfg, but I am afraid I could ruin it.

---

