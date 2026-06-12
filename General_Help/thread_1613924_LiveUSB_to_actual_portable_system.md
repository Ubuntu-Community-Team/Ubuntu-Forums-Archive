---
title: "LiveUSB to actual portable system"
date: 2010-11-05
forum: General Help
---

### Post by MyD0j0 on 2010-11-05
Hi, All.  First, thanks in advance to anyone who can provide assistance.  Second, this is not an advertisement. :D  Third, I really do eventually have a question...

Lets face it, there are a lot of pc users out there looking to be able to have a usb stick that can take all their programs and make them usable on whatever system they use.  Examples of the popularity of this desire is portableapps, Ceedo and Mojopac.  The first 2 are great in their own regard, but at the end of the day, they are not bootable self-contained systems.

But with the use of Linux Live USB Creator the true dream of portability is realized.  Not only does it allow booting to a self contained OS, but it allows having the same system to run in a normal MS Windows environment via VirtualBox--and virtualbox doesn't even have to be installed on the host system.  Throw in a larger than 4Gb casper-rw partition as detailed at pendrivelinux, and the only thing left to do is set up a sync for settings and files.  Do I hear angels singing from heaven?!?!

My question are: 


[LIST=1]
[*]on this Ubuntu pendrive, the user is the default 'ubuntu' with some unknown password.  I'd like to make the stick mine, not Ubuntu's.  When I add a user, why doesn't the home directory get the nifty subfolders that are in /home/ubuntu?
[*]When I boot the stick, it just goes straight to ubuntu account and does not seem to be able to be disabled so that I can log in using a user that I have defined.  How do I change this behavior?
[*]When I create a new user, should I be using the group ubuntu or admin (I'll be installing xampp then using eclipse on a regular basis)?
[/LIST]
Thanks!

---

### Post by garvinrick4 on 2010-11-05
It is a Live USB and or an install USB is not a installed system. Uses fat not ext as format and can be made up to 4 gig of persistence. Password is no password. Read up on squashfs and casper.

---

### Post by efflandt on 2010-11-05
The bootable iso on USB is primarily for testing and installation, and as you found out, is insecure unless you roll your own iso.  The kernel is fixed and initial boot is from a fixed squashfs file system that is mounted for init before persistent data (casper-rw) is mounted.  You can add programs, but cannot easily do updates of the kernel and other things that happen before casper-rw is mounted.

If you want a fully functional secure system, do a regular install to usb, but make sure that you put grub on the usb device.  Not sure if you can still do that on 4 GB, but 8 GB or larger is recommended if you do not want to be choked for space.  Then you can have a regular Linux file system, secure login, updates, etc.  Although, to minimize writing to flash you may want to use ext2 (no journal) or ext4 (with journal disabled), noatime for mounts, and tmpfs for /tmp if you have enough RAM, etc.

---

### Post by MyD0j0 on 2010-11-05
> **efflandt said:**
> The bootable iso on USB is primarily for testing and installation, and as you found out, is insecure unless you roll your own iso.  The kernel is fixed and initial boot is from a fixed squashfs file system that is mounted for init before persistent data (casper-rw) is mounted.  You can add programs, but cannot easily do updates of the kernel and other things that happen before casper-rw is mounted.

If you want a fully functional secure system, do a regular install to usb, but make sure that you put grub on the usb device.  Not sure if you can still do that on 4 GB, but 8 GB or larger is recommended if you do not want to be choked for space.  Then you can have a regular Linux file system, secure login, updates, etc.  Although, to minimize writing to flash you may want to use ext2 (no journal) or ext4 (with journal disabled), noatime for mounts, and tmpfs for /tmp if you have enough RAM, etc.


As it happens, the link i intended on leaving didn't get left...the normal casper-rw block file is replaced with an actual partition (ext2) and sized however large one may need: [Create a larger than 4Gb Casper Partition]("http://www.pendrivelinux.com/create-a-larger-than-4gb-casper-partition/"). I was able to update the system entirely and included a generic linux kernel update.

On the other hand, your second paragraph is what I'm talking about!  In searching the internet  to do that very thing, all that I ever found had to do with the live cd  stuff, which is ok I suppose, but useless in the sense of taking my  system to work, friend's house, library, or a kiosk--who wants to lug  around a laptop if they don't have to?  

I'm using a 16Gb flash drive--any tips on how to get the ubuntu installer to target the flash drive instead of my system disk?

---

### Post by nl4m on 2010-11-05
What you should do is download the ISO of the Ubuntu you want, burn it to a CD. The next step is VERY important. DISCONNECT any hard drives you have attached to the computer. If you do not disconnect it, grub will mess up the USB stick and the HDD. Next step is pop the disk in, shut the computer down. Pop the USB stick in, turn computer on and install the OS to the USB. I've done this at least 10 times. It works great. I can make my own name, set my own settings, and use the flash drive on any other computer.


> **MyD0j0 said:**
> Hi, All.  First, thanks in advance to anyone who can provide assistance.  Second, this is not an advertisement. :D  Third, I really do eventually have a question...

Lets face it, there are a lot of pc users out there looking to be able to have a usb stick that can take all their programs and make them usable on whatever system they use.  Examples of the popularity of this desire is portableapps, Ceedo and Mojopac.  The first 2 are great in their own regard, but at the end of the day, they are not bootable self-contained systems.

But with the use of Linux Live USB Creator the true dream of portability is realized.  Not only does it allow booting to a self contained OS, but it allows having the same system to run in a normal MS Windows environment via VirtualBox--and virtualbox doesn't even have to be installed on the host system.  Throw in a larger than 4Gb casper-rw partition as detailed at pendrivelinux, and the only thing left to do is set up a sync for settings and files.  Do I hear angels singing from heaven?!?!

My question are: 


[LIST=1]
[*]on this Ubuntu pendrive, the user is the default 'ubuntu' with some unknown password.  I'd like to make the stick mine, not Ubuntu's.  When I add a user, why doesn't the home directory get the nifty subfolders that are in /home/ubuntu?
[*]When I boot the stick, it just goes straight to ubuntu account and does not seem to be able to be disabled so that I can log in using a user that I have defined.  How do I change this behavior?
[*]When I create a new user, should I be using the group ubuntu or admin (I'll be installing xampp then using eclipse on a regular basis)?
[/LIST]
Thanks!

---

### Post by garvinrick4 on 2010-11-05
If you just want to do a normal grub install just choose sdb for grub install.
You have just the 16 installed in a USB port and your HDD. So HDD is sda and
16 gig is sdb
 When you update-grub in sdb you will be able to boot anything on sda also
If no linux grub installed on sda will not pick up sdb because of no linux on sda

Grub will not jump into HDD on its own unless you install it there sda (do not do it.)
So get it, when you boot sdb (16 flash as first in order will be able to boot  sda OS's on
sdb also. 
 When boot sda first just what is on that drive will boot. Anytime you stick 16 gig in another computer just 
```
sudo update-grub
```JUST INSTALL ON sdb and all is cool. Do not take your computer apart just focus on that one little thing.
Grub does not mess up anything, the user does by putting it in wrong place!! It is a good package grub2.

---

### Post by dcstar on 2010-11-05
> **efflandt said:**
> The bootable iso on USB is primarily for testing and installation, and as you found out, is insecure unless you roll your own iso.  The kernel is fixed and initial boot is from a fixed squashfs file system that is mounted for init before persistent data (casper-rw) is mounted.  You can add programs, but cannot easily do updates of the kernel and other things that happen before casper-rw is mounted.
.........

And to add to the Live USB limitations the casper-rw partition cannot have space recovered after deletions - so eventually it will fill up if you update enough programs/data on it!

AFAIK this is deliberate to extend the limited quantity of writes available on USB flash devices by continually moving them to different parts of the device.

---

