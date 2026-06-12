---
title: "Bootable USB doesn't boot."
date: 2011-12-22
forum: General Help
---

### Post by TheNerdAL on 2011-12-22
Going back to Ubuntu and tried to install it, but the bootable usb doesn't boot. :( I'm reinstalling the ISO right now, can anyone help?

---

### Post by TheNerdAL on 2011-12-22
i don't see any USB device in BIOS, only a Floppy Disk.

---

### Post by sammiev on 2011-12-22
Sounds like your system is rather old. I get a fast boot option at the bottom of my screen from the bios on boot. If I press F12 on the bios screen a boot menu appears where I can select USB or whatever.

---

### Post by killermist on 2011-12-22
Old bios?

Anything since 2008. I've had no trouble with USB booting (except for ambiguity due to additional USB drives)

---

### Post by Basher101 on 2011-12-22
If it is not in your BIOS, then USB boot is not supported...you will have to deal with the slower Live CD

---

### Post by Mark Phelps on 2011-12-23
IF you created the USB using unetbootin, that could be the problem.  I tried this recently and although it claimed to work, the resulting USB stick would not boot.  So instead, I downloaded the Universal USB Installer from PendriveLinux.com, used that -- and the resulting USB stick booted just fine.

---

### Post by HermanAB on 2011-12-23
There are some issues with USB booting.  Any live Fedora USB thingy boots on my Thinkpad, but neither Pendrive nor LinuxLiveUSB can make a thingy that will boot on that machine - though the thingies boot perfectly on another machine.

So YMMV apparently.

---

### Post by TheNerdAL on 2011-12-23
Found the settings to make the usb boot first! It was in the HDD section. :P

---

