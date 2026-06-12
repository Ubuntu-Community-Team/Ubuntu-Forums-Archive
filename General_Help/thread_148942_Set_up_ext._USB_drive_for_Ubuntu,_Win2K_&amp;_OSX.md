---
title: "Set up ext. USB drive for Ubuntu, Win2K &amp; OSX"
date: 2006-03-23
forum: General Help
---

### Post by cab1024 on 2006-03-23
I just bought a Metal Gear II USB2/Firewire housing and a 120GB HD. I put it together, plugged it into my Mac running OS X 10.4, which asked to initialize the disc. I agreed and it initialized it as a Mac OS Extended format. 

Ubuntu sees the drive and folders, but not the movie files in a folder created by Mac the Ripper on the Mac. I also do not have permission to access anything on the drive from Ubuntu.

The drive does not show up at all on a Windows 2000 box though it recognized the external housing as a new device, then the drive as a USB Mass Storage, and the name of the volume flashed by, but then it never showed up in My Computer.

How do I format the drive to work with all three systems so I can copy data back and forth between them all?

[I'm an Ubuntu newbie coming over fom Macs. I know even less about Windows.]

---

### Post by mjh007 on 2006-03-23
Try formatting the drive using the FAT32 filesystem. AFAIK this system can be read by all three OS that you mentioned.

---

### Post by nanotube on 2006-03-23
yea, at this point your best bet is fat32, like mjh says.

---

### Post by cab1024 on 2006-03-23
FAT32 does seem to be the one unifying format. But it is not as effecient with Macs as HFS+ (Mac Extended). I got Ubuntu to w/r to the drive by reattaching the drive to the Mac and changing the permissions for the drive and subfolders to read/write for everyone. So Mac and Linux is taken care of, which is the main thing.

I read about two apps, MacDrive and MacOpener, for Windows that allow t to w/r to HFS+ Mac drives. Does anyone know of a freeware app that does the same thing?

[The only modern box (w/USB2 or Firewire) I have is a Mac so I want it to run best with the Mac. It will be the writing drive for GarageBand recording.]

---

