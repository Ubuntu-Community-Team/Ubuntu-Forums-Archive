---
title: "20 failed attempts (literally) to install or fix"
date: 2010-03-13
forum: General Help
---

### Post by Gnusboy on 2010-03-13
Hello

If there is anybody out there who can help me get my system running I seriously need help
I have tried and tried to get Ubuntu up and running again after a fatal crash. Unknown reason.
I have burned several copies of Karmic and Jaunty, but the only one that will come up is an old copy of Jaunty Live CD. Chksum have matched on the disks and the disk integrity (the last time came up with 1 error, but it did not say where.
I have used SystemRescue64, Rescue-remix for Karmic, MHDD, Ultimate boot disk, and have reformated and partitioned my 640GB drive. One partition is formated to EXT3 and the other is unallocated. Both testdisk and memtest show positive.
No disk will complete a permanent install. At least one error shuts it down even after fixing broken packages and sometimes there are 3or 4 errors msgs.
Last night the error was something in Open Office, I don't recall more than that.

Here are the errors I picked out of todays logfiles. They are prety much in order as posted in the various logs:

 Kern.log file has a warning "tbutils-0217 incorrect checksum in table [oemb] -ef, should be e2 [20080926]

ata3 failed due to HW bug

chroot.c: open() failed: No such file or directory Failed to open /etc/resolve conf: invalid argument

console kit daemon[4169] Warning: couldn't read /proc/ 4168/ environ: no such file or dir.

Gnome-system-io segfault at1 ip 00007f7ccfd6a6ed error 4 in libgtk -x -2.0.s0.1600

[4913.691666] squashfs error: sb_bread failed reading block 0x1025d unable to read page block 408bed2 size 60c

I have also tried downloading Karmic through the command line I opened via Ubuntu rescue-remix 9.10 disk. It went through the entire process of d/l and install, but then failed the OpenOffice error.

System froze (very common lately) could not shut it down at 3:30 a.m. had to hardboot and close.

I am on my backup system, so I can't copy the logs - unless the system allows me to config and post to the forum. So far it just crashes. I will try and post the log files if I am successful.

I've been at this for more than 2 weeks and am completely stumped. I was going to take it to a tech in town, but most don't do Linux.

Any ideas?

---

### Post by revenant138 on 2010-03-13
Sounds like your hard drive or your connection to it is hosed...files disappearing, ATA problems...

---

### Post by MasterNetra on 2010-03-13
> **revenant138 said:**
> sounds like your hard drive or your connection to it is hosed...files disappearing, ata problems...

+1

---

### Post by dcstar on 2010-03-13
> **revenant138 said:**
> Sounds like your hard drive or your connection to it is hosed...files disappearing, ATA problems...

And check CPU/MB temperatures. Fans can get clogged up with dust, bearings wear out etc. Also MB components slowly die and become unreliable - nothing lasts forever.

---

### Post by Gnusboy on 2010-03-13
The system is about 7 months old and all diagnostics show that everything is working. I do not believe it is a hardware problem. Seems that Jaunty 9.04 worked fine and well. It was only AFTER in tried to upgrade to Karmic that problems started.

Hardware list:

ASUS M3A78-EM MoBo
Phenom 4X
4 Gb 800Mhz Ram
Western Digital 640 GB Hdd
Sony Optiarc 48X CD/DVD

Please Help me. It's more than 2 weeks and I just want to get this over or say screw it and buy a new copy of Winblows. I hate the idea, but XP and Win2K ALWAYS worked for me for years.
Save me from a return

---

### Post by viper250 on 2010-03-13
1st thing wipe your drive with d-ban 
this will clean the drive and test it 

repeated re installation will give you grub errors with out wiping the drives first
verify that your cables are seated properly and that your is getting adequate cooling.
an overly hot hdd can often cause errors

---

### Post by QIII on 2010-03-13
"Not old" does not mean "not broken".  Have you ever bought a new car that had to go back to the dealer for repairs within a few months of purchase?  Despite quality control at the OEM, some defective product does ship.

What you describe certainly leads me to suspect failing hardware.  I don't know what you are using for system diagnostics, but if all looks well there, it could very well be a failing hard drive.

Say you have a bad sector at some position, and it just happens to be that it is somewhere within the physical footprint of the OS.  There is no guarantee that the very same portion of the packages would hit that bad sector each time, so the errors you might get could vary each time.

As a poster said above, check your drive.  It is always best to eliminate hardware failure as a cause before beating your head against a wall trying over and over to install an OS that simply will not run because the hardware is faulty.

I would check the hard drive for errors.

If that is good, you might have a fault with the optical drive.

Check that the memory modules are properly seated.

Check that the video card is properly seated.

Check the power supply and all connections.

Don't trust "system diagnostics".

---

