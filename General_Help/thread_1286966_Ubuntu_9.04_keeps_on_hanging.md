---
title: "Ubuntu 9.04 keeps on hanging"
date: 2009-10-09
forum: General Help
---

### Post by Ganymedes on 2009-10-09
I have a problem in my Ubuntu system, which has been going on for some time now and I cannot find the cause for that.

What happens is that:
Suddenly, usually when dragging something from one window to another, the system "freezes".

What is freezing:
- keyboard does not seem to work. I even inserted an USB keyboard (when it froze), but it did not take that in
- I cannot select anything with a mouse, however the cursor moves
- Totem continues to play music - however, it will NOT change the track
- copying will continue (rsync, a possible interactive copy using the windows)


My system:
- motherboard Asus M2N-SLI, AMD 4850e processor, 64-bit
- Club 3D 8400GS 256MB GDDR2 PCI-E, a new, basic Nvidia card (with default Ubuntu drivers)
- 350 W power unit
- 2 GB Kingston memory
- EMU 0202 USB. That is usually in use, motherboard sounds are NOT disabled.
- external 1 Tb USB disk, Lacie Poulton (usually connected when it freezes, if not always)
- Ps2 keyboard, wireless USB mouse
- Ubuntu 9.04, 64-bit, upgraded from 8.10 (using Web)
- 3 SATA disks

What needs to be done (when it freezes):
- sometimes it continues after 5 minutes of waiting
- most of the time I cannot wait (or 5 minutes is not enough) and the only way is to cut the power from the system

What I have tried, without success:
- all the Ubuntu 9.04, updates are there
- flashed latest BIOS from Asus
- changed the file system on the external disk to EXT3 (was NTFS). That is usually in use when it freezes.
- tried with lesser SATA disks. All are EXT3.
- run Ubuntu (8.04 cd) memory checks
- changed memory from Kingston Valueram 800 MHz to Kingston Hyperthread (all 1 Gb units, 2 of them, 2 GB in all)

I am at loss what to try? ... other than wait for version 9.10 ... Obviously this is quite an irritating thing ...

---

### Post by PrePenguin on 2009-10-09
Which kernel are you using and if its the latest does it doit with a previous version of the kernel also?

---

### Post by superc0w on 2009-10-09
Haven't really researched it at all, but I've had very similar issues like this and it was my video card.  That'd be where I started looking first.

Good luck!

---

### Post by ajgreeny on 2009-10-09
Graphics card?  That can sometimes be a problem, but you don't say what you have in the machine.  Also you don't say if previous versions of ubuntu have run OK, or also hung when in use.

---

### Post by Ganymedes on 2009-10-09
Thanks!

Yes, I could have provided some more information on my system. Here are the answers:

1.
Graphics card, a very basic Nvidia card:
Club 3D 8400GS 256MB GDDR2 PCI-E

I am NOT using NVIDIA drivers. Should I, in this respect? Other than this, it works fine.


2.
Kernel, I hope I read it right from Synaptic Package Manager: 2.6.28-15.52. This is the latest regular update that I have got from the WEB. I use the normal WEB-update routines provided by Ubuntu.

And yes, it did freeze prior to this particular Kernel version.


3.
Did it freeze with 8.10?

Actually, I cannot say, since it was not really used much with that version.


Well, I could try with another graphics card, if this is a possible cause ... Thanks for the suggestion!

---

