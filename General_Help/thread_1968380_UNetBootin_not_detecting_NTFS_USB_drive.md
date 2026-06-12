---
title: "UNetBootin not detecting NTFS USB drive"
date: 2012-04-29
forum: General Help
---

### Post by Troxyn on 2012-04-29
Hey guys. I'm trying to make a USB installer for Windows 7 using UNetBootin. The problem is, the video I'm watching says to use GParted to format the USB stick to NTFS, except that when I do that, the drive's partition doesn't show up in UNetBootin. So, instead of NTFS I tried FAT32, which UNetBootin recognised, but when I insert it, it doesn't boot from it (and yes, I chose the 'boot' flag in GParted). Can anyone give me a hand?

And also, I did look at the boot order but the USB drive doesn't show up in it.

---

### Post by dino99 on 2012-04-29
[https://help.ubuntu.com/community/Installation/FromUSBStick](https://help.ubuntu.com/community/Installation/FromUSBStick)

---

### Post by 3togo on 2012-04-29
Try this
1. Download UNetBootin
2. Download  and install Win7 Syslinux Hack   
[http://ishan.jain.se/down/projects/Win7/Install/USB/Win7_Syslinux.exe](http://ishan.jain.se/down/projects/Win7/Install/USB/Win7_Syslinux.exe)
3. Use UNetBootin to copy files from Win7 ISO 
4. Extract zip to the root of your USB, overwrite syslinux.cfg

---

### Post by Troxyn on 2012-04-29
No, I'm trying to install Windows 7 on a USB IN Ubuntu, not the other way around.

---

### Post by Troxyn on 2012-04-29
Bump,

Anyone have a solution to this? I'm stumped.

---

### Post by garcher42 on 2013-02-01
Same thing happens on Mac OSX mountain lion with Paragon NTFS instsalled. I would love to know if you found a solution for it as it may apply to my situation as well.

---

### Post by tworette on 2013-06-30
The problem is the version of Unetbootin, I think. Seems you have to use an older one, see here:
[http://www.linuxandlife.com/2012/12/unetbootin-create-bootable-usb-windows-7.html](http://www.linuxandlife.com/2012/12/unetbootin-create-bootable-usb-windows-7.html)

---

