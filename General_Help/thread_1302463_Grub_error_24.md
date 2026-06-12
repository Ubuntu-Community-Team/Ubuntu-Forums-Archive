---
title: "Grub error 24"
date: 2009-10-27
forum: General Help
---

### Post by suresh_ecer on 2009-10-27
Hello, 
I recently installed Ubuntu 9.04 along side my windows xp. Now when I reboot, grub gets stuck at stage1.5 with grub error 24 sometimes 15 and sometimes it gives 23. 
 
Now i m not able to run either XP nor Ubuntu, my PC turns in to a dead body. 
I have also tried to overwrite XP over it but windows setup not able to access my Harddisk but it is running fine on live session (On CD) and i m able to retrive my all data. 
 
I have also tried with win98 bottable disk to fromat harddisk but same problem occurs.
I m not able to boot XP, Ubuntu ; Not able to format it and even i connect my harddisk as a slave with another PC but same things repeat.
 
Any one please suggest how i can recover my pc back in to working condition.
 
Thanks & Regards,
Suresh Chauhan

---

### Post by tomBorgia on 2009-10-27
I'd say you have a hardware problem with your harddisk... If you can't format it in windows, ubuntu or as a slave disk it'll need replacing.

Tom.

---

### Post by martrn on 2009-10-27
First read the following : [https://help.ubuntu.com/community/WindowsDualBoot]("https://help.ubuntu.com/community/WindowsDualBoot").

Secondly understand about the boot sequence [http://en.wikipedia.org/wiki/Boot_sequence]("http://en.wikipedia.org/wiki/Boot_sequence").  You boot the computer in two stages, the bios boots the bootloader, the bootloader boots the kernel, the kernel sets the environment loads necessary kernel modules and gives you a desktop or logon screen.

If grub is working properly you should be able to boot a kernel or another boot loader.   Your error messeages indicate that grub can not find a suitable kernel and necessary files that it needs and is a requirement to boot an OS.  Hence it can not load a kernel.

You need to re-install grub, (or a bootloader) or change the grub configuration files which grub will fetch as part of its 1.5 stage of loading.  So to recover your system you will need to :

- Boot into a windowze CD, Restore the windowze MBR so it can boot windowze and then copy the first five hundred and twelve bytes of the ubuntu partition (grubstage1.5)  to the windowze drive as ubuntu.bin so that it can boot the ubuntu kernel.[[http://www.matthewjmiller.net/howtos/dual-boot-linux-and-windows/]("http://www.matthewjmiller.net/howtos/dual-boot-linux-and-windows/")]

-- OR --

- Boot into an unbuntu CD, Restore/Re-Install GRUB to the MBR and the the first 512 bytes of GrubStage1.5 to the ubuntu partiton so that it can boot ubuntu kerenels and windowze, check the grub files are properly configured and pointing to the correct drives.  [[https://help.ubuntu.com/community/WindowsDualBoot]("https://help.ubuntu.com/community/WindowsDualBoot")]

Grub is defunct / not working properly / broken.

---

### Post by tomBorgia on 2009-10-28
Yes martrn may be right... I was thinking you may have used ubuntu's format which, well, works as opposed to windows (win98???) format which is, well fussy...

---

