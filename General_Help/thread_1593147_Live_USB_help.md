---
title: "Live USB help"
date: 2010-10-11
forum: General Help
---

### Post by jan1024188 on 2010-10-11
I've been trying to get Ubuntu 10.10 on my laptop, so I used live usb creator ([http://www.pendrivelinux.com/downloads/Universal-USB-Installer/Universal-USB-Installer.exe](http://www.pendrivelinux.com/downloads/Universal-USB-Installer/Universal-USB-Installer.exe)) to copy image there and when I was installing ubuntu installer crashed saying files are corrupted.

So I decided to use dd and try:
[root@localhost jan1024188]# dd if=/dev/sdb of=/home/jan1024188/Downloads/ubuntu-10.10-desktop-i386.iso 
4063232+0 records in
4063232+0 records out
2080374784 bytes (2.1 GB) copied, 83.5852 s, 24.9 MB/s
[root@localhost jan1024188]# 

But when I try to boot usb nothing happens... :S Help (Im using Fedora 12).

---

### Post by jan1024188 on 2010-10-11
oh dumb me, I confused if and of...

---

### Post by jan1024188 on 2010-10-11
I ALWAYS ALWAYS confuse if and of....now I have to download again :S

---

### Post by TheAnachron on 2010-10-11
I had some issues with the USB creater too, since my system does not seem to like booting from USB.
Try burning it on a CD/DVD instead. Its faster as well.

---

### Post by jan1024188 on 2010-10-11
ok, dd has failed. Any suggestions what I should do?

---

### Post by jan1024188 on 2010-10-11
meh I give up, got syslinux failing, installer crashing etc. Maybe this release was too rushed or something, it doesn't seem to be working "out of box" for me...will wait for Fedora 14 and stick to it :P

No distro is perfect, but @ least I know what can I get to work on fedora and what not (only things failing me in Fedora 12 are mobile broadband and nvidia 3d drivers).

---

### Post by alexfish on 2010-10-11
hi

could only get the iso install ( the live cd with persistent did not work )

try to use a usb stick 4g or less

from the usb creator select the " Discard on shut down unless you save them somewhere else"

if using sticks larger the 4g , wipe it clean including the boot sector flags

---

### Post by C.S.Cameron on 2010-10-11
Check the MD5SUM of the iso.
Try UNetbootin to make the Live USB.

---

