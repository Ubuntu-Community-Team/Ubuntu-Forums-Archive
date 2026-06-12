---
title: "Problem booting from USB disk installation"
date: 2011-04-09
forum: General Help
---

### Post by catmanduo on 2011-04-09
Folks,
 
Sorry if this is already covered. I'm having trouble using Ubuntu 10.10 (64 bit)
to create an installation on a USB (read-write) drive.
 
I've had to use PLOP to boot the system, since I want the usb drive on a high-speed
controller, and my machine is such that the on-mainboard USB is slow.
So, I put the empty USB (16 GB) on the fast controller, boot from the Ubuntu installation DVD, and install the OS.
 
Then I switch to booting PLOP, the boot manager, and use it to boot from USB.
Everthing works fine, and I can use ubuntu -- but only the first time.
 
Once I shut down, and try to boot again, PLOP doesn't start the boot from
the USB drive. It apparently crashes (the star field simulator doesn't continue).
It does try to (at least) load the USB drivers, but stalls without finding the USB boot
medium (my flash drive).
 
Anyone have any idea what's happening? Also let me know if there might be a more
trusted way to boot from the high-speed USB drive (like, it would be great if 
the installation disk had an option to install the USB drivers and then do a secondary 
boot). Plop is nice because it can be on read-only storage (a DVD or CD) and
so can't be corrupted after the fact.
 
Catmanduo

---

### Post by Bcrowes11 on 2011-04-09
You're trying to run from the usb permanently?

---

### Post by catmanduo on 2011-04-09
Yes.  This is the first step to trying to get a read-only installation.
Initially I'm just trying to use a USB flash drive as a read/write installation.
 
Cat

---

### Post by Bcrowes11 on 2011-04-09
so maybe you screwed up the usb...try reburning the iso...also make sure the md5sum is correct...

---

### Post by tweaktolive on 2011-04-09
you cannot use the usb flashdrive because whatever changes you make on ubuntu , after shutting down it changes it to default because the changes are in the RAM rather than the USB.

---

### Post by catmanduo on 2011-04-09
No, I'm not using the utilities that make a "live" image.
I'm just using the flash as a disk drive (for now).
So changes should be preserved -- the only problem is that something
is changing that is making it unbootable.
 
Cat

---

### Post by catmanduo on 2011-04-09
Ok, here's another data point for everyone.
 
I've used the USB live disk creator (usb-creator-gtk I think) to create a "live"
image of the raw distribution on a flash drive.  Then I flick the read-only
switch on that flash drive (once I've removed it).  THAT thing boots up fine multiple times.
It's only the read/write installation, where I'm trying to use a flash as a disk drive
(read/write) that the first boot somehow makes it non-bootable.
 
Cat

---

### Post by catmanduo on 2011-04-09
By the way, is there a way to compare an ISO with a real drive image?
Maybe that would help, but since I'm using "install" instead of creating a 
(duplicate, presumably) live image, it might be harder to see what's going on.
But it would be useful to me to know how to burn an ISO, flip the read-only switch,
and then make sure nobody got to it before I flipped the switch.

---

### Post by C.S.Cameron on 2011-04-09
What is this read only switch?
I don't think there is a way to make a persistent install read only that way.
I hope you are not using Update Manager on a Persistent Live USB, the drive will quickly fill and once full will be unbootable.

---

### Post by catmanduo on 2011-04-09
Cameron,
 
Sigh -- I'm adding tmi.
There are USB flash drives with a read-only switch (hardware read-only).
And yes, you can't just take a normal install and make it readonly.
There's another post that says how to create a live DVD from an installed
system, which is another form of readonly install.
I will do something similar to put a live DVD isntallation on the readonly USB flash drive, when the time comes.
 
Right now, I'm just having trouble getting a normal installation to boot twice.
I'm using a flash drive as a normal disk, albeit I have to use something like
PLOP to boot from the USB flash, since I want it on a fast controller.
 
Cat

---

