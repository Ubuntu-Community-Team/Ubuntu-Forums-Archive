---
title: "USB drive problems and Ubuntu installation."
date: 2010-06-22
forum: General Help
---

### Post by lifeindecember on 2010-06-22
Hey all. I'm trying to create a USB drive installion with Ubuntu 10.04 on it so I can update from Xubuntu 8.04. 

Unfortunately I can't even get the USB to appear. I'm new to xubuntu/ubuntu so I know that drives need to be mounted or something, but my 500Gb external drive showed up just fine when it was switched on.

Also, does xubuntu not come with the Startup Disk Creator? I can't seem to find it if it does.

Thanks in advance.

---

### Post by ram2500 on 2010-06-22
I haven't used Xubuntu, so I'm not sure if it does come with the Startup Disk creator utility, however, if the flash drive isn't showing up, you might want to try formatting it. In Xubuntu you might have the Disk Utility application (similar to Disk Management in the Management Console in Windows)--and you should be able to format it if you can't mount it. The utility has a strange name (Palimpset?) and if if you don't have it: sudo apt-get palimpset (or whatever the proper spelling).

I'm sure you can also get the startup disk utility, but I'm not sure of its package name. You'll need either a Ubuntu CD or a downloaded ISO of Ubuntu to be able to create an Ubuntu key--you won't be able to make a startup key without an image to copy from.

---

### Post by J V on 2010-06-22
The package is usb-creator-gtk, I don't think it came with the distro back in '08

---

### Post by C.S.Cameron on 2010-06-22
Last time I looked, a few years ago, Xubuntu did not come with or work with usb-creator.
You could try:
sudo apt-get install usb-creator.
Or you could try UNetbootin, LinuxLive, the offerings from pendrivelinux.com or a grub2 iso install.

The installer should be able to find your pendrive ok.

---

### Post by lifeindecember on 2010-06-22
So while I was away eating dinner with some friends, the usb stick apparently mounted itself. I came back and it was mounted just fine and open in the file manager. Apparently I've got some Xubuntu-using goblins living in my house.

I can't find the Startup Disk Creator though.

when I try:
> drew@Watchtower:~$ sudo apt-get install usb-creator
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package usb-creatorSame for 'usb-creator-gtk,'.
> drew@Watchtower:~$ sudo apt-get install usb-creator-gtk
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package usb-creator-gtk


Aslo, I want to make it clear that I'm not trying to make a usb stick that I can take places to run Ubuntu off of. I'm trying to make a usb stick to INSTALL Ubuntu on the desktop I'm using now. I'd make a CD but everytime I try, I get an error that the media is busy.

---

### Post by C.S.Cameron on 2010-06-22
Probably easiest to go with Unetbootin in that case, it should work with Xubuntu.

---

