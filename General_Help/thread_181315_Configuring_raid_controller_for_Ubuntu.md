---
title: "Configuring raid controller for Ubuntu"
date: 2006-05-24
forum: General Help
---

### Post by louiemctool on 2006-05-24
Greetings!

I'm trying to install Ubuntu on a Compaq Proliant 3000.  I can get the first half of the install to work, but when the machine attempts to reboot it hangs when trying to kill all processes.  If I simply do a forced shutdown, the installer crashes down to the UNIX shell when it tries to load Ubuntu after the reboot.

The server uses a Compaq SmartArray2 PCI raid controller, which communicates (I'm assuming) with the raid module.  I only have one hard drive installed right now, but it can take up to 12.

It seems mostly that the Ubuntu installer can't 'see' the raid module, but I'm over my head, so I hope someone can point me to the right info.  Thanks in advance for any suggestions!

Here's the 411:

Compaq Proliant 3000 (Cabinent Mounted version)
Dual Pentium III 550MHz slot 1 processors w/ VRMs
1.5GB ECC RAM (PC66, I think)
one 36.x 10,000 RPM hard drive
IDE floppy & CD-ROM
PCI Compaq SmartArray2 raid controller

---

### Post by bodycoach2 on 2007-05-31
I have recently acquired a Proliant 3k, PII 300 Mhz system myself. I followed the instructions on [THIS ]("http://advosys.ca/viewpoints/2007/04/setting-up-software-raid-in-ubuntu-server/")page, and set up RAID 1 with no problem at all. I tried to do by myself first, with the same result as you. I may try a reinstall, just to see if I can set up RAID 0 following the same procedure, but selecting RAID 0 in the selection process.

This is definitely a skill that has to be practice much before mastered.

I have links about my setup experience in [my blog ]("http://coachdanny.blogspot.com")too.

---

### Post by regomodo on 2007-06-01
[https://help.ubuntu.com/community/FakeRaidHowto](https://help.ubuntu.com/community/FakeRaidHowto)
[https://wiki.ubuntu.com/FakeRaidEdgy](https://wiki.ubuntu.com/FakeRaidEdgy)
[https://help.ubuntu.com/community/FakeRaidDebug](https://help.ubuntu.com/community/FakeRaidDebug)

Did you have to use drivers for this setup in win server? If so, the controller isn't a true hardware raid controller, i believe. If it's a true hardware controller you setup the raid in bios (before os boot) and the OS sees the setup as a whole drive

I'm not very clued up about it but it's something i'm looking into atm

---

### Post by louiemctool on 2007-07-24
Thank you both for your replies.  I no longer need the specific information I requested, but I appreicate the effort anyway!

---

