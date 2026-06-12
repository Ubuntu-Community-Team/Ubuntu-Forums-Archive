---
title: "RAID Migration to Ubuntu (latest build, 8/24/10)"
date: 2010-08-24
forum: General Help
---

### Post by minigts on 2010-08-24
Hi all,

I have a hardware RAID that was setup on a previous build of windows, but the OS crashed (not the drives) and now I can't view the files at all on XP.  The original build had the OS loaded onto the RAID, just as a note.  I tried installing XP on an entirely different drive and then hook the RAID back up but to no avail.  You can see the drive in the MMC, but it will not read it without formatting it first, which I don't want to do.  So I thought I would install Ubuntu on the same setup hoping it would see the RAID, but my extreme limited knowledge of Linux has me at a loss on how to even establish a RAID setup or view an existing build hardware RAID.

Can someone point me in the right direction on how to load drivers for an existing hardware RAID in Linux or better, possibly do this in Windows?

The board is an Intel D975XBX with the Silicone Image RAID controller.  The board also has an Intel based RAID controller, but I've tried both sets of drivers and it obviously sees the drives, but it won't recognize the actual RAID as a drive to access.  Any advice would be greatly appreciated.


This is the controller, not Intel.  Sorry if I confused anyone or said something incorrectly.  Silicon Image SiI 3114

---

### Post by ronparent on 2010-08-25
This looks like a typical 'fakeraid' setup (that's what the community calls it). If you have installed Ubuntu 9.10 or 10.04 or using the live cd for those versions the drives should be found and made mountable automatically. This is by virtue of dmraid which come with and automatically installs a program called dmraid. Dmraid serves the same purpose in Ubuntu as the drivers serve in windows. Try downloading and burning Ubuntu 10.04 to a cd or dvd if you haven't already done so. Boot to it, when the first screen appears hit any key to complete the boot to the live cd, and, see what you find. You might want to come back to ask more question or get some tips on how to install to a raid, if that is what you intend. Have fun.

Edit: Note - You can look to you hearts content with out fear of harming anything valid on those raid drives. If you want to install or modify anything on the raid you should call for help.

---

