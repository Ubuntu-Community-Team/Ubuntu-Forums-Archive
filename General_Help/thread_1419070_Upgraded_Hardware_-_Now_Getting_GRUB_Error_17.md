---
title: "Upgraded Hardware - Now Getting GRUB Error 17"
date: 2010-03-01
forum: General Help
---

### Post by kulturloseramerikaner on 2010-03-01
I had this thread over in Upgrades/Installations and haven't gotten any replies; perhaps I put it in the wrong category.

I moved last summer and the mobo on my old system didn't survive the trip. I finally got around to getting myself a new processor and mobo a week ago, but I haven't been able to fully restore my system.

I was happily triple-booting 8.04, PC-BSD, and Win XP before, and each on its own hard disk. I decided to add Win 7 as I got it on the cheap to have a game playing platform. After the build, the install of Win 7 went off without any issues. I've added back the drives containing the other 3 os's though, and am now having trouble.

Even after removing the cable to the Win 7 drive and putting the original 3 drives in the correct (I'm pretty sure) SATA ports, I get GRUB error 17. This but isn't even the weird part; GRUB itself loads to the selection screen but trying to boot either 'nix system is no good, it says it can't read either the 'Buntu or BSD drives (invalid file system type). If I tell it boot XP though, it gives me the XP splash screen no problem, then BSOD's because it doesn't yet to know what to do with the new mobo/processor combo (I'd like to resolve the boot issue before I run an XP repair install if I can.)

I'd like to get myself able to boot all 4 os's; currently I'm able to use Win 7 as long as I pull the SATA cables to the other 3. Supergrub has not helped, nor has downloading 9.10 to liveCD because of the GRUB2 switch there (can't find my 8.04 disk.)

I'd greatly appreciate any help or pointers to get me going in the right direction on this. I miss my Linux too much.

---

### Post by kulturloseramerikaner on 2010-03-02
I got Ubuntu back; I couldn't find an Ubuntu LiveCD in my stash with 9.04 or previous on it, but I did come across an older Sabayon LiveCD stashed away that allowed me to make the necessary modifications to my menu.lst file. :D

Now the problem is, I can boot the original 3 os's if I have the SATA cable to the drive containing 7 unplugged; otherwise, it boots straight to 7. Changing the order of the drives (changing the location of the SATA cable on the mobo from port 0 to 1 for example) does not affect this behavior though it made a difference on the system I just upgraded from. Is there something I've forgotten to do that will force the BIOS to look to the GRUB partition first? 7 plays nicely with previous versions of Wintendo, is there a way to configure GRUB to chainload into the 7 bootloader and choose the flavor of Wintendo from there, and does anyone know if running a repair install on the 7 side will allow me to see the XP install?

---

