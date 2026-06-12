---
title: "Won't Boot from USB"
date: 2010-01-11
forum: General Help
---

### Post by RobChap on 2010-01-11
I am trying to install ubuntu netbook remix onto my ASUS 900A EeePC using a 2GB Flash drive that has been formatted to FAT32.  I used Linux's USB Startup Disk Creator and ubuntu-9.10-netbook-remix-i386.iso to make the flash drive (hypothetically) bootable.  
 
I went into the BIOS and changed the Boot Device Priority to boot from the Flash Drive first.  
 
However, when I try to boot from the Flash Drive, I get the following message: "Reboot and Select proper Boot device or Insert Boot Media in selected Boot device and press a key".  I tried removing and reinserting the flash drive and pressing a key, but the same message keeps popping up.  I tried the above process with another, 1GB, flash drive, and got the exact same result.
 
I know the computer is capable of booting from a Flash Drive because I got it to boot from my friend's 4GB SanDisk flash drive when installing ubuntu 9.04.  
 
Any suggestions?

---

### Post by nishant.singh28 on 2010-01-11
Do you, by chance have any other USB storage device connected to the system when trying to boot from the USB. It so happens that the system has its own way of selecting the USB device. It happened with me and then I saw that my Portable HDD was connected and my Laptop was trying to boot from it.

---

### Post by RobChap on 2010-01-11
Do you, by chance have any other USB storage device connected to the system when trying to boot from the USB
 
No, just the flash drive.

---

### Post by sharp11 on 2010-02-23
I am having the same problem on an Eee PC. Did you ever solve it?

---

### Post by Sven6210 on 2010-02-23
[COLOR=black][FONT=Verdana]Hello,[/FONT][/COLOR]
[COLOR=black][FONT=Verdana] [/FONT][/COLOR]
[COLOR=black][FONT=Verdana]I have an Asus EeePC 900a and I do not have any problem booting from an USB device. I did not even change the boot priority in the BIOS.[/FONT][/COLOR]
[COLOR=black][FONT=Verdana] [/FONT][/COLOR]
[COLOR=black][FONT=Verdana]When you get the start screen of your EeePC (the white one of the BIOS which is shown before the OS starts to load) you need to press the 'Esc' button. Then you will get a menu where you choose from which USB device you want to boot.[/FONT][/COLOR]
[COLOR=black][FONT=Verdana] [/FONT][/COLOR]
[COLOR=black][FONT=Verdana]When I do not hit the 'Esc' button my Ubuntu from the SSD is loaded automatically. I never had problems booting from USB and I actually do it regularly as I have d dedicated and write protected USB stick with a special Ubuntu version that I only use for online banking – this avoids trojans and virus issues and increases security.[/FONT][/COLOR]
[COLOR=black][FONT=Verdana] [/FONT][/COLOR]
[COLOR=black][FONT=Verdana]Best regards[/FONT][/COLOR]
[COLOR=black][FONT=Verdana] [/FONT][/COLOR]
[COLOR=black][FONT=Verdana]Sven[/FONT][/COLOR]

---

