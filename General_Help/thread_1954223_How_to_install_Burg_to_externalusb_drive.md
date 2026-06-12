---
title: "How to install Burg to external/usb drive?"
date: 2012-04-07
forum: General Help
---

### Post by corelx on 2012-04-07
Here is a solution for installing Burg bootloader to an empty - or without linux installed - drive!
First you will need a Live-CD or USB, i've used a 10.04 Ubuntu LiveUSB.
After got on to the desktop open up a terminal and mount your drive (where you want to put the Burg) under the /mnt folder. Next issue the following commands, assuming you're in the /mnt:
```
sudo su
mkdir bin cdrom dev dev/pts etc home lib media proc rofs sbin sys usr tmp var
mount --bind /bin ./bin
mount --bind /cdrom ./cdrom
mount --bind /dev ./dev
mount --bind /dev/pts ./dev/pts
mount --bind /etc ./etc
mount --bind /home ./home
mount --bind /lib ./lib
mount --bind /media ./media
mount --bind /proc ./proc
mount --bind /rofs ./rofs
mount --bind /sbin ./sbin
mount --bind /sys ./sys
mount --bind /usr ./usr
mount --bind /tmp ./tmp
mount --bind /var ./var
chroot /mnt/ /bin/bash
add-apt-repository ppa:bean123ch/burg
apt-get update && apt-get install burg

```
The Burg install process will do everything, and should finish with no errors.
In case you missing something from the menu, you can add it to the end of the /boot/burg/burg.cfg and rerun the update-burg cmd.
Just to be sure, check your Burg install with the burg-emu command!

You can leave now the chroot with exit, and umount all the binds, and remove the folders. Except the ./boot, there is the Burg inside :)

Hope it's useful somebody!

@Dcstar
Nothing is impossible with linux ;)

---

### Post by hal8000 on 2012-04-07
You should not have to compile Burg add the following repos:

[https://help.ubuntu.com/community/Burg](https://help.ubuntu.com/community/Burg)

Have never tried to install BUrg to an external drive, but works fine on internal partitions or MBR on my SATA2 drive.

---

### Post by dcstar on 2012-04-08
> **corelx said:**
> 
I've been working on Burg to install it somehow to a external drive,
but **haven't found the way to get it work**...
After some googling found many solutions about installing
grub to external hd, but none of them worked for the burg.
Which makes it hard, that **this device doesn't have ubuntu installed**,
........

Burg - and Grub - **require** a Linux installation to work.

You are wasting your time trying to "install" a boot loader without all of its requirements.

---

### Post by corelx on 2012-04-08
Thank you guys for the quick answers!

Actually an hour ago i've managed to install it
on the device :guitar:

sudo burg-install --force --no-floppy --root-directory=/mnt/SDCARD /dev/sdb

The files and folders are created, but at the boot it's
only get me the burg command line (exactly like the grubs).

I think something is still missing, hopefully i can solve
it today.
If you have additional idea, please share it :)

---

### Post by corelx on 2012-04-08
Read first post!

---

### Post by hadora on 2013-01-15
Doesn't work for me, when i chroot /mnt/ /bin/bash i get the error " no such file or directory "

See my thread [http://ubuntuforums.org/showthread.php?t=2105224](http://ubuntuforums.org/showthread.php?t=2105224)

---

