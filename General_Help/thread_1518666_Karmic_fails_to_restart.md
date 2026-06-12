---
title: "Karmic fails to restart"
date: 2010-06-26
forum: General Help
---

### Post by UserName108 on 2010-06-26
Hi,

Have been running Karmic 910 for six months on a Dell Latitude D510 laptop with a Pentium M CPU, 2 GB of RAM and Intel 915 graphics, and I really like it, especially the Gnome desktop.  However, a glitch occured after suspending, resuming, shutting down and trying to restart.  Now after selecting Ubuntu in Grub the Ubuntu logo shows up onscreen, doesn't pulsate, and eventually is replaced by an error message that the system gave up waiting for root device.  

The LiveCD shows the Ubuntu partition as unrecognized, unknown or unused in Palimpsest Disk Utility, though Gparted shows it as normal ext4. The partition doesn't show up in Places.  From the command prompt (via ctrl-alt-F1) I'm able to run fdisk, which shows the partitions but am unable to mount the Ubuntu sda4 partition - the error message is that the file type must be specified.

Starting recovery mode in Grub brings about 25 lines of startup messages, mostly dealing with usb devices, but a few render errors are there too.  The last message before dropping to the ash shell is that a device could not be found. (ALERT! /dev/disk/by-uuid/5cee... does not exist.)  The ash commands are completely new to me, so I haven't had any luck with recovery mode.

I would like to try some "quirks" (software fixes for hardware problems, including Intel graphics bugs) mentioned on the ubuntu.wiki site and recover the data on the desktop, but so far cannot get into the file system. 

Would reinstalling without formatting anything preserve the data?

Would upgrading to Lucid help prevent the problem from occurring again?

Thanks.

---

