---
title: "I'm selling my computer - how do I remove Ubuntu?"
date: 2011-08-03
forum: General Help
---

### Post by r3think on 2011-08-03
Hey guys, I am currently dual booting Windows 7 and Ubuntu. I am selling my computer and the buyer wants only Windows 7 on the computer. How do I get rid of the ubuntu partition? And how do I get back to the regular windows bootloader (not grub)?

Thanks!

---

### Post by Synoc on 2011-08-03
reinstall the software it came with. AKA the Rescue disk. for information on how we need to know what make/model you have

---

### Post by r3think on 2011-08-03
Thinkpad T420

---

### Post by Furball588 on 2011-08-03
I'd probably just use omething like bootsect or bcdedit to take care of the MBR so you don't have to use grub to boot into windows.  

Obviously reboot when to make sure it doesn't boot into grub, then just remove your ubuntu partitions via disk management.  If you feel the need, then re-expand your HD so windows uses the entire drive.

---

### Post by Synoc on 2011-08-03
K, while I'm looking up the options, go find your rescue disks.

---

### Post by r3think on 2011-08-03
Restore disks? Is there any way for me to return the Thinkpad to factory settings without disks?

Also, could I delete the ubuntu partition (from a live cd)? Would that get rid of grub?

---

### Post by Synoc on 2011-08-03
You can completely wipe the disk with a live boot, yes. but without the factory disks, you can't reset to factory specs, if you formatted the hard drive with ubuntu, LIKELY. you MIGHT have a protected partition that's still there on the hard drive. either escape or one of the F keys would be able to access it. but I don't know which on your PC. that's what I'm looking for

---

### Post by linuxuser12345 on 2011-08-03
Have you considered keeping Ubuntu on? I think it can almost be a fact that all Windows users care about computer viruses and prefer *not* to have them.

But, if you want to remove Ubuntu, I would pop in an Ubuntu liveCD or liveUSB, and go the the Disk Utility or GParted program. Click on the Ubuntu partition and click "format". ONLY format the Ubuntu partition. Format it as a FAT or NTFS file system.
I am not sure if you can merge the two partitions back together, but I am sure someone in this forum knows.

---

### Post by wojox on 2011-08-03
Run dban and then a fresh install of Windows 7.

---

### Post by Furball588 on 2011-08-03
> **r3think said:**
> Also, could I delete the ubuntu partition (from a live cd)? Would that get rid of grub?

It would, but there's also a bit that still resides on the MBR that points back to that grub directory that isn't removed...and subsequently will error because the directory is not there if you delete the partition.  

That's why I suggested using bootsect or bcdedit first.  


If you're going to restore route, there's no need to go this way btw.

---

### Post by Synoc on 2011-08-03
> **linuxuser12345 said:**
> Have you considered keeping Ubuntu on? I think it can almost be a fact that all Windows users care about computer viruses and prefer *not* to have them.

But, if you want to remove Ubuntu, I would pop in an Ubuntu liveCD or liveUSB, and go the the Disk Utility or GParted program. Click on the Ubuntu partition and click "format". ONLY format the Ubuntu partition. Format it as a FAT or NTFS file system.

if that does not work. I hope this does

[B][http://forum.notebookreview.com/lenovo-ibm/222246-restore-ibm-thinkpad-factory.html](http://forum.notebookreview.com/lenovo-ibm/222246-restore-ibm-thinkpad-factory.html)

[/B]if you have the recovery partition, that will reset it to factory specs.

---

