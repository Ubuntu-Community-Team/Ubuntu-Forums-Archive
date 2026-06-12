---
title: "Access USB device!!!????"
date: 2010-10-14
forum: General Help
---

### Post by DavidFelix on 2010-10-14
I just installed Linux 10.4. I put my VC++ Projects on my USB device. I installed Device Manager; it appears there but i'm not able to access my files. It doesn't show up in the /media directory. How can I access my files? Help, please and thank you.


-Platanos :)

---

### Post by DavidFelix on 2010-10-15
50+ views and no one knows? How do you connect your devices?

---

### Post by Refalm on 2010-10-15
Could you describe this "device manager" you installed?
You don't need it. When you insert an USB stick, you can just access it from locations, and it shows up at the desktop.

I recommend uninstalling this "device manager", since it's most likely very old. The website of gnome-device-manager is gone, so it's probably not maintained.

Also, you have installed Ubuntu 10.04, not "Linux 10.04".

---

### Post by nothingspecial on 2010-10-15
```
sudo fdisk -l
```Figure out which you usb device is, some thing like /dev/sdb1 (I will use that for example, change it for what it actually is)

```
sudo mkdir /media/usb
```You need to know what file system your usb thing is, I will assume FAT

```
sudo mount -t vfat /dev/sdb1 /media/usb
```Your files are now in /media/usb, but they will be owned by root

```
sudo chown -R username:username /media/usb
```Now you will own them.

I am assuming you have the server edition installed.

---

### Post by DavidFelix on 2010-10-15
Nothing Special! These were the results:

sudo: fdisk-l: command not found

God, I needa switch back :/

---

### Post by nothingspecial on 2010-10-15
> **DavidFelix said:**
> Nothing Special! These were the results:

sudo: fdisk-l: command not found

God, I needa switch back :/


My fault, there is a space between fdisk and -l

```
sudo fdisk -l
```

---

### Post by DavidFelix on 2010-10-15
Thanks! This is what came up:

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       29370   235912192   83  Linux
/dev/sda2           29370       30402     8284161    5  Extended
/dev/sda5           29370       30402     8284160   82  Linux swap / Solaris

---

### Post by nothingspecial on 2010-10-16
Is your usb device plugged in.

If not do it again, also do

```
lsusb
```

```
and dmesg | tail -n 20
```

after you plug it in

---

