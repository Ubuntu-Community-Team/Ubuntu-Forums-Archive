---
title: "Grub2 and Expresscard and Windows 7"
date: 2010-04-20
forum: General Help
---

### Post by LaferriereJC on 2010-04-20
I got Grub2 to recognize my express card by using the --disk-module=ata during install.

Only problem is, it seems to only work when loading Ubuntu (of course the kernel has to be recompiled with the phison module to successfully boot, see [http://swiss.ubuntuforums.org/showthread.php?p=9144366](http://swiss.ubuntuforums.org/showthread.php?p=9144366) )

When grub2 is in ata mode, my devices come up as (ata8,1) respectivelly.

I tried ghosting a copy of windows onto the expresscard and booted with grub2, but when I do a

set root=(ata8,1)
chainloader +1
boot

I get a "disk read error occured" error, press ctrl+alt+del to reboot, and nothing, can't even reset machine.

Be aware that I did test this with a non "--disk-module=ata" install using "set root=(hd0,1)" and it does boot into windows 7, but when the grub2 is in "--disk-module=ata" mode, I get an error when trying to boot.

I'm not sure if the "ata install" of grub2 is ntfs incompatible or what?  In fact, the only thing I can successfully boot is linux, I've tried fat32, but the system either reboots or locks up.

I have once installed xp onto the expresscard and used win7rescuepe to find a windows xp installation (uses grub4dos) and it found th xp installation, when it tried to boot it said something about an incorrect hard drive configuration that was preventing setup from continuing.  However, I don't know how grub4dos even saw the expresscard to begin with.

---

### Post by Mark Phelps on 2010-04-20
If the express card is essentially an external drive, you might want to go to sevenforums.com to check into their tutorials about Win7 installs.  

While you may be able to install Win7 to an external drive, I don't believe you can boot it from one.  But, the Win7 forums will have more detailed information.

---

### Post by LaferriereJC on 2010-04-20
thanks for the forum, someone else asked a similar question in 2009 in July ([http://www.sevenforums.com/installation-setup/18993-install-ssd-expresscard.html](http://www.sevenforums.com/installation-setup/18993-install-ssd-expresscard.html)), w/no responses.

There is a rather lively forum on boot-land.net (when it works) about expresscard's and windows 7, trying to treat it like a usb drive, but I think I've gotten the furthest with grub2 actually seeing the device (as far as I can tell, there trying grub4dos, and so far for me, grub4dos can't see the expresscard.)

This problem is just a matter of getting grub2 to boot from it without a "disk read error", which seems to be a problem with the "disk-module=ata" installation which is required to see the expresscard.  The way I know it's a "disk-module=ata" problem, is when I'm in this mode I can't boot from a non express card either (as in a regular hd).  If there was a grub2 forum, I'd post there.  If there was an expresscard forum, I'd post there.  I'm already active on boot-land, so I decided to branch out.  Anyone an expert with grub2?

If it does get past the disk read error to some sort of windows boot error message, then I can move on to the next step, which is the "kansas city shuffle"
[http://www.boot-land.net/forums/?showtopic=4186](http://www.boot-land.net/forums/?showtopic=4186)

---

### Post by interfect on 2010-04-28
I need to do this as well. I want Linux on my internal drive, and Win7 on an external eSATA drive connected via an ExpressCard. I went to the Grub IRC channel on Freenode and was told that I "may be able to load a kernel from the drive directly if the drive can be accessed in IDE compatibility mode." I get the feeling that this is unlikely to work well for booting Windows.

Any progress?

Is there anyone who can provide a tutorial on how a "Kansas City Shuffle" from Linux Grub to Win7 might be accomplished?

Can I surreptitiously replace the Windows bootloader with Grub, or install the Windows equivalent of /boot onto the internal drive, in order to make this work?

---

### Post by Mark Phelps on 2010-04-29
> **interfect said:**
> ... Can I surreptitiously replace the Windows bootloader with Grub ...

Basically -- no.  GRUB only hands off control to the Windows boot loader; it is not capable of booting Windows.

---

