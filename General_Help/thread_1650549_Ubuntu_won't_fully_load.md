---
title: "Ubuntu won't fully load"
date: 2010-12-21
forum: General Help
---

### Post by rugabug on 2010-12-21
I have 10.04 on my Desktop and it worked fine till a few days ago when I installed a bunch of libraries.
Now when I turn on my desktop it stays where it shows the login screen minus the window used for login and never gives me the chance to login.
I used my laptop to make a bootable usb drive for 10.10 and it hangs on the progress bar/scrolling dots screen. I've tried two different usb drives and 2 different mirrors for the iso.
Windows xp loads just fine
Most of my thesis work is saved to the desktop so I can't just do a clean format and reinstall.

---

### Post by garvinrick4 on 2010-12-21
Put in a install Cd and choose try Ubuntu: When it boots run:
```
sudo fdisk -l
``` (lower case L)
find your ubuntu install lets say it is sda1 for this example: (Use your own sda#)
```
sudo mkdir /media/root
``````
sudo mount /dev/sda1 /media/root
```Now Hit alt/f2 and when box opens type gksudo nautilus hit enter:
nautilus will open in root. click on your mounted install on left of nautilus.
Open your home and then where your files are, documents or where ever.
Drag and drop them to xp install or usb flash, something to hold them.
Close nautilus and Open a terminal and:
Get your internet connection with network manager applet.
Below is to get into your install and update and try and fix dependencys
update grub. Copy and paste these in terminal one at a time:
```

[CODE]sudo mkdir /media/root/dev
``````
sudo mkdir /media/root/dev/pts
``````
sudo mkdir /media/root/proc
``````
sudo mkdir /media/root/sys
``````
sudo mount -o bind /dev /media/root/dev
``````
sudo mount -o bind /dev/pts /media/root/dev/pts
``````
sudo mount -o bind /proc /media/root/proc
``````
sudo mount -o bind /sys /media/root/sys
``````
sudo cp etc/resolv.conf /media/root/etc/resolv.conf
``````
sudo chroot /media/root
``````
dpkg --configure -a
``````
apt-get update && apt-get upgrade
``````
dpkg --configure -a
``````
update-grub
``````
exit
``````
sudo umount /media/root/dev/pts
``````
sudo umount /media/root/dev
``````
sudo umount /media/root/proc
``````
sudo umount /media/root/sys
``````
sudo umount /media/root
``````
sudo reboot
```[/code]

---

