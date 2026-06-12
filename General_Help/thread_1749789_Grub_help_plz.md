---
title: "Grub help plz"
date: 2011-05-04
forum: General Help
---

### Post by JigglyWiggly_ on 2011-05-04
Ok, I've been sitting here for like 5 hrs.
[http://ubuntuforums.org/showthread.php?p=10769924](http://ubuntuforums.org/showthread.php?p=10769924)

Ok, here is my setup:Laptop hd, 320 gigs, SD card 32 gigs(cannot boot from BIOS into SD card)I installed Linux onto the SD card.

Ok, so I install Windows 7 onto the hard drive. Now I want to get rid of the Windows boot loader and install the fabulous(****) GRUB.

But how do I do this? I boot off the livecd, and try grub-install /dev/sda, it doesn't let me. I try sda1, sda2, nada.

What am I supposed to do?

Help plox? All the discussions are on dual booting and recovering, but there is nothing to recover here...

---

### Post by garvinrick4 on 2011-05-04
You have to have an installation with the grub files in them for grub loaded in mbr (master boot record) of sda to look for. If you have just Windows 7 it does not use grub2 so does not work on its own. 
Ubuntu uses grub2 (grub-pc), Fedora it uses grub (grub legacy) and Windows it has its own
version of a Bootloader, BCD I believe it is called nowadays.
Grub2 has a program called OSprober that reaches out and installs other operating systems into the grub config file and as a menu entry.

---

### Post by LostFarmer on 2011-05-04
I do not think grub itself will boot to a USB device if the bios does not permit it. There might be ways around it, but have not tried.
1) Put a small linux boot partition on the internal hdd , it will need the grub files and vmlinux and intrd files. (all files/directories in the normal /boot.), the rest of linux will be on the SD card.

2) try plop  [http://www.plop.at/en/bootmanager.html](http://www.plop.at/en/bootmanager.html)

Could read up on grub4dos , it might but do not think so.

That is if I'm reading your problem correctly.  Understand I have NOT tried any of the above, so it is a guess.

---

### Post by JigglyWiggly_ on 2011-05-04
I think you're right about GRUB not being able to boot to a SD card
EDIT: O wait, [http://ubuntuforums.org/showthread.php?t=986126&page=2](http://ubuntuforums.org/showthread.php?t=986126&page=2)


Will try this, hopefully works on grub2 and not too many problems.

---

