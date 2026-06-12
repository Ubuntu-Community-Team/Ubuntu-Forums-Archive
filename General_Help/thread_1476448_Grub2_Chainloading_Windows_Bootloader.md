---
title: "Grub2 Chainloading Windows Bootloader"
date: 2010-05-07
forum: General Help
---

### Post by marksoccer on 2010-05-07
I've browsed through the forums and couldn't find a working solution to my problem.  I have installed grub2 to the mbr of sdb and the windows 7 x64 bootloader to the mbr of sda.  Windows 7 boots fine if I set the bios to boot sda first.  However, when I try to chainload hd0's mbr from grub2, the screen blinks and then returns to grub.  If I try to chainload hd0,1 I get a black screen with a blinking white cursor that just sits there.  I have tried using drivemap and everything to no avail.  Does anyone have a solution to this problem?

---

### Post by mechro on 2010-05-07
I'm not sure if this helps but in Grub Legacy if you booted sdb that would be hd0 and sda would be recognised as hd1.

---

