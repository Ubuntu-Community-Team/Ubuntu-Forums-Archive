---
title: "Install Parted magic on USB from Live CD"
date: 2010-03-08
forum: General Help
---

### Post by ushpiy on 2010-03-08
Hello!

I want to install Parted Magic on my USB drive from my GParted live Cd.
I don't want to install any OS. I have tried the procedure on Parted Magic's site but it hasn't helped.
I am new to Linux so please be kind enough to help me.

Note:
I am mainly stuck at this step:
> [FONT=georgia]In Linux, write the Syslinux MBR to the USB drive (this is not needed when you have already a bootable MBR on the USB drive). A copy of mbr.bin is included in the USB version of Parted Magic. It's located in boot/syslinux. Change directory to the root of the USB drive that the Parted Magic files were copied to, and use this command:[/FONT]
[COLOR=DarkRed][B]
cat  boot/syslinux/mbr.bin > /dev/sdx[/B][/COLOR]
This file is located in this place on my PC as taken from the GParted file manager address bar
/media/Leopard/Users/Piyush/Desktop/untitled folder/pmagic-usb-4.8/boot

Ummm... Could anyone write a command for this?
Thanks a ton!

---

### Post by Techsnap on 2010-03-08
Post the output of:

```
sudo fdisk -l
```

---

### Post by ushpiy on 2010-03-09
Thanks for the help but I managed to resolve the issue myself.

---

