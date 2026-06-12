---
title: "installing ubuntu from flash drive?"
date: 2010-06-18
forum: General Help
---

### Post by creative31 on 2010-06-18
I have one quick question, When using a flash drive to install Ubuntu, it says you need 2 gigs of space, will it affect the installation if I only have 1 gig of space?

Thx
Creative

---

### Post by oldfred on 2010-06-18
Do not know. Perhaps it expands some of the files.

But I found this an alternative way that works. I am using a 4GB Flash but have 7 installs all as ISO files that I can choose. I have 3 full Ubuntu, mini, system rescue, gparted & pmagic. I also have some room for data. Grub will act as a mini boot operating system and then loop mounts the ISO file.

MultiBoot USB with Grub2 (boot directly from iso files)
Is full script, I only used some commands
[http://www.panticz.de/MultiBootUSB](http://www.panticz.de/MultiBootUSB)
 HOWTO: Booting LiveCD ISOs from USB flash drive with Grub2 
[http://ubuntuforums.org/showthread.php?t=1288604](http://ubuntuforums.org/showthread.php?t=1288604)
Basically you just install grub2, create a folder for the isos and edit a grub.cfg to loop mount the isos.

---

### Post by AndrewRenn on 2010-06-18
> **creative31 said:**
> I have one quick question, When using a flash drive to install Ubuntu, it says you need 2 gigs of space, will it affect the installation if I only have 1 gig of space?

Thx
Creative

Yes, you can install Ubuntu 10.04 (and probably other versions) with a 1GB flash drive. I did my install with a 4GB drive, and still have >3GB's remaining, and it says I only used 700 MB.

Good luck with the install, and make sure to have another computer around just in case you have any problems!

---

### Post by C.S.Cameron on 2010-06-18
Just do not select the persistence feature if you have a problem.

---

