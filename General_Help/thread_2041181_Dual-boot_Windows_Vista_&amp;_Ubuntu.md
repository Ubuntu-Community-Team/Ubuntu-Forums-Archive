---
title: "Dual-boot Windows Vista &amp; Ubuntu"
date: 2012-08-12
forum: General Help
---

### Post by Shadius on 2012-08-12
Hey everybody! :)

I'm wondering if there's a way to dual-boot Windows Vista, which is on my Acer Aspire 5920 laptop, with Ubuntu on an external hard disk drive. However, I want it so that when I plug in my external hard disk drive, Ubuntu is displayed on the bootloader, I'm guessing it'll use GRUB, and when I unplug my external hard disk drive, the only option will be Windows. If so, how? 

My thinking is that I would make a partition for Ubuntu in the external hard disk drive, say 250 GB, boot from the Ubuntu LiveCD using my laptop, use the "Something else" option, create / (root) and swap space within that 250 GB partition that I previously made, install the bootloader to the Windows Vista hard disk drive, and...?

I need to be thorough with this because my Windows Vista never came with an installation disk, so if I mess this up and Windows Vista gets deleted, then that's it for Windows. I still need Windows for a few things so I can't have that happening. I'd appreciate it if you could give me detailed explanations. Thank you very much.

---

### Post by decrepit on 2012-08-12
If you can get into bios and get it to boot from the external HD, you can install grub on the external HD, so when the hd is plugged in you'll get the grub bootloader. When it's unplugged it'll default to the internal HD and you'll get the windows boot loader.
I've done something like this when I was testing various distros and had them installed on their own HDs.

---

### Post by Mark Phelps on 2012-08-12
The safest thing to do is have the internal drive disconnected when you install Ubuntu to the external drive.  That way, you won't risk the installer forcing GRUB onto the internal drive.

---

### Post by oldfred on 2012-08-12
You definitely want grub2's boot loader installed to the MBR of the external drive.
You may want to add a NTFS shared data partition on the external to backup or share data from Windows when in Ubuntu. Best not to directly write into the Windows system partition any more than you have to.

The vendor recovery DVDs are just an image of your drive as purchased. If you have housecleaned a lot of cruft normally included, run many updates with many reboots, and added software you may want a full back up.
Backup windows before install - post by Mark Phelps
[http://ubuntuforums.org/showthread.php?t=2040149](http://ubuntuforums.org/showthread.php?t=2040149)
[http://ubuntuforums.org/showthread.php?t=1626990](http://ubuntuforums.org/showthread.php?t=1626990)
[http://www.macrium.com/reflectfree.asp](http://www.macrium.com/reflectfree.asp)
Another suggestion by srs5694
[http://www.runtime.org/driveimage-xml.htm](http://www.runtime.org/driveimage-xml.htm)

Make your own Windows repairCD (not vendor recovery):
[http://windows.microsoft.com/en-GB/windows7/Create-a-system-repair-disc](http://windows.microsoft.com/en-GB/windows7/Create-a-system-repair-disc)
[http://forums.techarena.in/guides-tutorials/1114725.htm](http://forums.techarena.in/guides-tutorials/1114725.htm)

Windows 7 repair USB, Also Vista if service pack installed
[http://www.intowindows.com/how-to-repair-windows-7-from-usb-flash-drive-repair-without-installation-dvd-disc/](http://www.intowindows.com/how-to-repair-windows-7-from-usb-flash-drive-repair-without-installation-dvd-disc/)
[http://www.webupd8.org/2010/10/create-bootable-windows-7-usb-drive.html](http://www.webupd8.org/2010/10/create-bootable-windows-7-usb-drive.html)

---

### Post by Shadius on 2012-08-12
Okay, what about this: I plug my external HDD into my Ubuntu desktop computer and install Ubuntu on the HDD that way. I install the bootloader to the HDD, and then will I be able to use my HDD with Ubuntu on any other computer that I plug it into?

---

### Post by sienile on 2012-08-12
I would think that you would have to have similar hardware on any computer you try to run it on. To be able to run it on any computer you should make a GRUB entry for a LiveCD iso. There's a recent post on this forum that gives a link to a tutorial on this. I'll post back if I find it.

---

### Post by sienile on 2012-08-12
Found it a lot faster than I thought I would. :D

[https://help.ubuntu.com/community/Grub2/ISOBoot]("https://help.ubuntu.com/community/Grub2/ISOBoot")

---

### Post by Shadius on 2012-08-16
Thank you.

---

