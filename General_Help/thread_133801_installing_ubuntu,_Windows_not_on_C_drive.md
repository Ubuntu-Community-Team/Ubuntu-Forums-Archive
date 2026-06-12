---
title: "installing ubuntu, Windows not on C: drive"
date: 2006-02-20
forum: General Help
---

### Post by Chimona on 2006-02-20
I want to install Ubuntu on the C: drive. i have windows on the E: drive, but i'm worried about ntdetect and ntldr, anybody know how i can put them on drive E: with the rest of windows. or do i even need to? 

please help

---

### Post by saudoi on 2006-02-20
Don't worry, when u install Ubuntu, new boot loader (LILO or GRUB) will come so that u don't need NT-boot loader (ntdect and ntldr).

You can't install Ubuntu into drive C because it is formated as FAT or NTFS, not compatible with Ubuntu. You should delete partition C to create a free space and install Ubuntu into this free space.

Hope that help.

---

### Post by saudoi on 2006-02-20
Chimona can get more information in this site:
[http://users.bigpond.net.au/hermanzone/](http://users.bigpond.net.au/hermanzone/)

Ps: I got it from the signature of one member, say thank to him :)

---

### Post by Chimona on 2006-02-20
Thanks for the speedy and helpful response!

---

### Post by RAOF on 2006-02-20
[QUOTE=Chimona]I want to install Ubuntu on the C: drive. i have windows on the E: drive, but i'm worried about ntdetect and ntldr, anybody know how i can put them on drive E: with the rest of windows. or do i even need to? 

please help[/QUOTE]
And well you should be worried about ntdetect & ntldr.  They'll have been placed on your C: drive (because windows is brain-dead and absolutely refuses to boot from anything but the first partition).  I'm not sure how you should proceed.  You could try removing (almost) everything from your C: partition, then shrinking it (to 50 Mb or so - easily enough for ntdetect etc) using the Ubuntu partitioner in the install process and installing Ubuntu into the free space there.

That would keep your XP boot stuff in the place windows expects, and still allow you to install Ubuntu.

Edit: I'm *pretty* sure that windows requires some of the ntdetect/ntldr in order to boot, whether or not you use grub/lilo - Grub/lilo don't know how to boot windows, they just pass the buck on to the native bootloader.

---

### Post by Chimona on 2006-02-20
A

---

