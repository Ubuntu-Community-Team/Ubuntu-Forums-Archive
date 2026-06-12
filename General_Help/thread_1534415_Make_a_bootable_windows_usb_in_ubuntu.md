---
title: "Make a bootable windows usb in ubuntu"
date: 2010-07-19
forum: General Help
---

### Post by ali999 on 2010-07-19
Hi

I need to install windows on my netbook in order to run some programs i need for school. I currently have Ubuntu 9.10 installed on here and am trying to make a bootable windows 7 usb. Does anyone know how I can do this? Thanks in advance.

---

### Post by computerguts on 2010-07-19
Is it a 64 or 32 bit operating system?

---

### Post by ali999 on 2010-07-19
32 bit windows 7 pro.

i have the cd contents currently copied to my hard drive.

---

### Post by rubylaser on 2010-07-19
The easiest way to do this would be to copy your Windows 7 install DVD with dd
```
dd if=/dev/cdrom of=/home/<username>/windows7.iso
```
or if your netbook dosen't have a DVD drive, copy the folders to .iso using mkisofs
```
sudo apt-get install cdrtools
```

```
mkisofs -V label-name -r directory > iso-image.iso
```


And, then use the Ubuntu built-in tools to make a USB disk.
[IMG]http://www.pendrivelinux.com/wp-content/uploads/make-usb-startup-disk.jpg[/IMG]

Hope that helps.

---

### Post by Joe of loath on 2010-07-19
If you have the .iso file, unetbootin MIGHT work. I can't say I've ever tried it, but I know it works for boot floppies up to windows XP.

---

### Post by C.S.Cameron on 2010-07-19
1. sudo apt-get install gparted
2. open gparted -> format stick to ntfs
-> put bootable flag (right click in gparted - manage flags)

3. extract win7.iso to usb stick or if you have live dvd just copy contents to usb stick

from Amedac

---

