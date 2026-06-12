---
title: "Printer not accessible in VirtualBox"
date: 2010-08-16
forum: General Help
---

### Post by yendorian on 2010-08-16
Hi, I am running virtualbox 3.2.8 and whilst I can use my USB keyboard my Canncon LIDE scanner, USB exble ternal hard drive and a logitech joystick I cannot access my Cannon IP4700 printer or Samsung laser printer.

All my USB devices are recognized in the vbox settings nut are not recognized by guest win7 0r xp-pro any clues?

---

### Post by todak on 2010-08-16
Did you download the drivers and install them from Win7 while in VirtualBox?

---

### Post by Ginsu543 on 2010-08-16
Can you see your hard drive listed under Devices --> USB Devices in the VirtualBox menu? If so, has it been greyed out? If true, then it means that your main OS is using it and hasn't released it. Try unplugging your printer from the USB and plugging it back in. If not, try deleting your printer in System --> Administration --> Printing.

---

### Post by yendorian on 2010-08-17
> **todak said:**
> Did you download the drivers and install them from Win7 while in VirtualBox?

Yes I have the drivers on disks for windows and installed them whilst in VirtualBox windows indicates that the printers are ready to print but then try to print to a file. Trouble shooting says the printer is not connected.

---

### Post by yendorian on 2010-08-17
> **Ginsu543 said:**
> Can you see your hard drive listed under Devices --> USB Devices in the VirtualBox menu? If so, has it been greyed out? If true, then it means that your main OS is using it and hasn't released it. Try unplugging your printer from the USB and plugging it back in. If not, try deleting your printer in System --> Administration --> Printing.

My USB hard drive is listed and the NTFS partition on it is accessible by Windows (guest), I have tried as you suggest unplugging and replugging and disenabled them in Ubuntu but no luck. Both printers work fine in Linux and in a stand alone windows.

---

### Post by Jett Deion on 2010-08-17
Any printer can be networked, but the bigger, faster printers are often  advertised a network-ready because they are more suitable for shared  usage, and may even have an integrated server-interface card.

---

### Post by mooscape on 2010-08-21
I have been having trouble connecting from XP guest (virtual box on Ubuntu) to my networked printer on NAS server. I managed to get it up and running via cups, and would like to share this cheatsheet if others could use it.(Or should this have its own post as a howto?)

---

