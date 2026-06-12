---
title: "can't make the USB bootable"
date: 2010-05-09
forum: General Help
---

### Post by attilab on 2010-05-09
trying to install a dual boot to my new Asus 1500PE netbook what came with some limited ver. W7.
tried 3 different scenarios (from XP laptop):
- usb creator won't select the stick, wont work for me.
- unetbootin create-finish, but not booting no one machines XP or w7
- universal-usb-installer create-finish but not booting no one machine
The stick is the 4Gb Lexar, prior operation formated to Fat32.
the image file ubuntu-10.04-netbook-i386.iso was chacked for integrity all OK. 
The installation files are there on the stick what these aps copy over.
I made changes to both laptop BIOS and shall boot from removable storage.
I check from XP and W7, execute the wubi.exe on the stick and the CD boot helper starts, but this is not a CD, its the stick. 
I checked from XP Temp folder (where I extract the iso file) the wubi.exe has different graphycal interface, and menu.
Im running out with my options, must be something simple what I've overlooked.
to create the bootable USB from my ubuntu 8 Im not enough trained with that yet, step by step instruction more than welcome.

---

### Post by redcodefinal on 2010-05-10
Try formatting the stick in exFat.

---

### Post by attilab on 2010-05-10
solved, in weird way, thanks anyway
the BIOS in this netbook seem to me have to roll 2x
1. F2 and changed the BIOS to boot from Removable Device
log in to W7, execute the wubi on the stick
it will ask if I can't boot from stick will give me a hand, so installs something arround
restart with the stick in place, F2
2. now I could see that there is an extra-new option for boot from USB what need to check again,
restart and the rest is known
this might be a help to a new Asus 1500PE netbook user who want to istall a dual boot from USB

---

