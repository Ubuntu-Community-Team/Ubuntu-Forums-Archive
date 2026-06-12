---
title: "Cant boot any other OS after ubuntu install"
date: 2010-12-26
forum: General Help
---

### Post by nickd123 on 2010-12-26
I formatted my whole entire drive and installed ubuntu 10.10 but i have been having some problems such has webcam,drivers,wireless shutting down randomly,brightness,settings not saved etc i tried to boot off my usb drive to install xp but i get this black page saying something like SYSLINUX and some other stuff cannot find Kernal image and some more stuff and i just get a command line. This happens when i try to boot any OS if it has something to do with the bootloader i never think i installed one i just formatted the drive and installed ubuntu and when it boots i get a flashing _ and it boots. please help

---

### Post by efflandt on 2010-12-27
You need to change boot order in BIOS for USB to boot before internal drive.  And even if you do that, you may still have to press a key during the BIOS (often Esc or F12) splash screen to select boot from USB (to avoid accidentally booting anything potentially malicious).

---

### Post by nickd123 on 2010-12-27
> **efflandt said:**
> You need to change boot order in BIOS for USB to boot before internal drive.  And even if you do that, you may still have to press a key during the BIOS (often Esc or F12) splash screen to select boot from USB (to avoid accidentally booting anything potentially malicious).

ive dont that yet it still does that

---

### Post by nickd123 on 2010-12-27
> **nickd123 said:**
> ive dont that yet it still does that

i have dont that but i sitll get the error

---

### Post by nickd123 on 2010-12-27
> **nickd123 said:**
> i have dont that but i sitll get the error
I have done that yet i still get a error

---

### Post by efflandt on 2010-12-27
What do you have on your USB drive and how did you install it?  The SYSLINUX thing makes it sound like you had a Linux live/install iso on it, but files for that are missing now.  SYSLINUX would not have anything to do with WinXP (which would use a regular DOS/Windows mbr)?

Is that USB drive able to boot on any other computer?

---

