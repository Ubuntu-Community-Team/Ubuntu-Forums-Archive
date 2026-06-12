---
title: "Ubuntu 10.10 install blew away Windows"
date: 2010-10-15
forum: General Help
---

### Post by NoMax2 on 2010-10-15
:mad: I'd been away from Ubuntu for a while so I decided to give 10.10 a try.

My PC: Asus Commando, 2 x 1TB disks as RAID 1, 1 x 320GB Non-RAID disk. Running Windows Vista 64 bit on the RAID voulme.

I booted the installation CD and selected "Install Ubuntu", then "use entire disk". At the next menu I selected the installation location as the 320GB non-raid disk.  Install went fine.

At reboot there was no bootloader, the system appeared like it was going to boot right into Windows - then BSOD.  It flashed so quickly that I couldn't see the error message - then the PC rebooted - caught in a loop over and over again.

I then booted the Vista DVD in an attempt to repair the bootloader - as I thought this was the only thing wrong.  I couldn't repair it - tried loading the RAID drivers and nothing.  No Windows installation was found.  

I used the Vista DVD to boot to a command prompt and holy %$&#, every Windows file was deleted from my system.  I was left with a few large files with long filenames like 88546-87464-262627 (not really one of the names).  Thank the powers that be that my personal folder seemed to remain intact.  I'm now in the process of recovering all my family photos and music through the DOS prompt with XCOPY.  If I would have lost that it would have been a total disaster.

Well - I always wanted an excuse to go to Windows 7 - this is as good as any - but WHAT HAPPENED?????  I'm still in the process of copying my media over but I'm pretty upset.  I don't think I'll be messing with Ubuntu again :(

Is it possible to recover Windows from this?  WHAT HAPPENED?  How did Windows and all my EXE files get wiped and my photos and music remain intact???

---

### Post by NoMax2 on 2010-10-15
I solved the problem.  I disconnected one of my RAID disks and booted the machine. It came up with the Grub Rescue prompt. I then disconnected the RAID disk that gave me the Grub Rescue prompt and connected the other one. I got a message that Windows was unable to boot and to use my Windows DVD to recover.  I tried it and was then able to boot into Windows with a single RAID disc.  All my files were there, everything worked.  I turned off the PC and connected the 2nd RAID disk back up.  The RAID controller went into REBUILD mode and Windows came up.

So evidently there is some incompatibility with Grub and the RAID controller in my Asus Commando motherboard.

Now I'm thinking if Ubuntu is on my non-raid disk (it should be) and if so - how could I boot into it without messing with the bootloader on my RAID array?

---

