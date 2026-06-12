---
title: "PenDriveLinux - For Linux??"
date: 2010-11-12
forum: General Help
---

### Post by Roasted on 2010-11-12
I'm trying to take several .ISO's (Ubuntu, Clonezilla, GParted, UBCD, and several others) and put on a large flash drive I have here. I have tried many utilities, and they all in some degree didn't work.

I keep finding PenDriveLinux in my google searches, but all I can see is a .exe Windows downloader for this. What. Really? I mean, that just doesn't add up. I know some companies like VMWare are foolish enough to pride themselves in being Linux based yet they don't have a Linux vsphere client. Is PenDriveLinux in the same boat? Is there a Linux download for it so I can run it in Ubuntu and set it up the way I like?

---

### Post by oldfred on 2010-11-12
I just used grub2 to loop mount several ISO on my 4GB flash drive. I did a full install on my 16GB flash drive but have added one or two ISOs to it the same as my 4GB drive.  I did it manually but now some have scripts that install several ISOs. 

 HOWTO: Booting LiveCD ISOs from USB flash drive with Grub2 
[http://ubuntuforums.org/showthread.php?t=1288604](http://ubuntuforums.org/showthread.php?t=1288604)
Basically you just install grub2, create a folder for the isos and edit a grub.cfg to loop mount the isos.

MultiBootUSB - Install and boot multiple Linux from Pendrive / Flash drive / USB disk 
[http://ubuntuforums.org/showthread.php?t=1518273](http://ubuntuforums.org/showthread.php?t=1518273)

multicd.sh - combine Linux ISOS into one
[http://ubuntuforums.org/showthread.php?t=1071869](http://ubuntuforums.org/showthread.php?t=1071869)

older MultiBoot USB with Grub2 (boot directly from iso files)
Is full script, I only used some commands
[http://www.panticz.de/MultiBootUSB](http://www.panticz.de/MultiBootUSB)

---

