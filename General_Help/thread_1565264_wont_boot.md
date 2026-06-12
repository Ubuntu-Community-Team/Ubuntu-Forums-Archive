---
title: "wont boot"
date: 2010-08-31
forum: General Help
---

### Post by lizzard8 on 2010-08-31
Hello! I have a problem i cant seam to solve myself. I installed ubuntu 10.04.1 server edition on a computer the other day. And i did this with a usb drive. To my knowlage everythig went fine during the installation.
 
The problem is that ubuntu wont boot unless i leave the usb drive in. Without the usb in i get disk boot failure. I want to be able to just boot the thing up from the harddrive. I currently only have one hard drive connected.
 
I created the usb with Universal-USB-Installer-1.7.9.1 from [www.pendrivelinux.com]("http://www.pendrivelinux.com")
 
I am used to windows os and know basic things about linux os. keep it in mind.
 
what can i do to solve this?

---

### Post by ktemkin on 2010-08-31
Well, your first problem seems to be that you're not making it into any bootloader.

Ensure the partition where the bootloader in question is installed is "active" by ensuring its boot flag is set. You should be able to easily do this from GParted, which comes on the LiveCD.

If that's not your issue (which is likely), I'd suggest [recovering GRUB2]("https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows"), the default linux bootloader.

You can follow that guide using your live disc.

---

### Post by andrewthomas on 2010-08-31
The bootloader is on the usb drive.

Follow the instructions here.

[https://help.ubuntu.com/community/Grub2#Reinstalling%20GRUB%202](https://help.ubuntu.com/community/Grub2#Reinstalling%20GRUB%202)

---

### Post by lizzard8 on 2010-08-31
SOLVED
 
I thank u from the bottom of my heart! (=
 
I reinstalled grub2, booting ubuntu from a separate usb.
And it worked like a charm!

---

