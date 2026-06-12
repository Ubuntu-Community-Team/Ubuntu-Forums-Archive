---
title: "odd question here"
date: 2011-08-26
forum: General Help
---

### Post by christopher.wortman on 2011-08-26
Someone I know is paying me $300 to install Windows Server 2008 R2 Enterprise onto a server.

Every Sata port is taken up by a 2tb hdd and its all raided so no optical drive.

How do I bit copy the ISO on Ubuntu to a thumb drive? I don't have a Windows install to speak of in my house... I am not going to buy a USB DVD drive just for this because it will probably never get used ever again. I isoed the DVD up at work and took the iso home, he has the license I just gotta figure out how to get it onto the system and I can figure out how to configure it to his needs...

---

### Post by christopher.wortman on 2011-08-26
Does anyone know if this is possible to do with Unetbootin?

---

### Post by christopher.wortman on 2011-08-26
This is a really useful walkthrough that worked for me

1) using KDE Partition Manager, make the USB stick NTFS
2) Safely remove the drive then take it out and put it back in (wont show up in unetbootin)
3) Select Diskimage and click the 3 dots (...) and find the ISO (of Windows)
4) Click "show all drives" and select /dev/sdd1<-- really important you select the mounted partition for some reason it shows both the actual device and the partition. It will fail out and say something about not having enough space.
5) Click OK, then wait, make some popcorn come back when it's done (takes a few minutes on install.wim)
6) Boot the intended system with the USB disk in from the boot menu

VOILA Windows install disk without DVD!

---

