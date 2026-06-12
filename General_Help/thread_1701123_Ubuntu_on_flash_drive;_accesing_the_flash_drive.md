---
title: "Ubuntu on flash drive; accesing the flash drive?"
date: 2011-03-06
forum: General Help
---

### Post by your_average_bro on 2011-03-06
I have an Ubuntu 10.10 LiveCD installed on a flash drive, and it boots fine and everything, but I can't access the flash drive from within Ubuntu.

Even though its booted from it, I should still be able to access it, right?

I've tried 'fdisk -l' and even GParted, and it doesnt even detect my flash drive as being plugged in.

All other OSes I use allow you to access whatever media it booted from; just because you booted from it, doesnt mean it should 'lock it down'.

Anybody know how I can access the flash drive from within Ubuntu?

Thanks.

---

### Post by Hedgehog1 on 2011-03-06
The LiveCD and and USB version of the LiveCD is running a casper (Ghost) image that is loaded into RAM.

If you wish to use your USB drive as a Pocket PC (a.k.a **Ubuntu-On-A-Stick!**), you need to install Ubuntu from a CD onto the USB stick acting as your hard drive.

The basic steps are:

(1) With the power off, disconnect your hard drive(s).
(2) Power up with the USB stick inserted and boot off the LiveCD; choose the install option. The USB drive will be used as the hard drive.
(3) Reboot when install tells you too, but don't run the updates until you delete the **/etc/grub.d/30_os-proper** file.  Deleteing it will keep the GRUB on the USB stick from adding your OS(s) on your hard drive in future updates.
(4) Run the updates. When they are complete:
(5) Power off and plug you hard disks back in.

***The Hedge***

:KS

---

### Post by coldraven on 2011-03-06
Did you create a persistence file on your flash disc?
If you didn't then this might work.
Copy the Ubuntu iso to your hard drive.
Then re-boot from a Ubuntu Live CD..
Run System>Admin>Startup Disk Creator.
Make sure you check "make persistence file" and choose how much space it has.

---

### Post by C.S.Cameron on 2011-03-06
If you are booting from a Live USB you need to go to filesystem/cdrom to see the actual files that are on it.
If you want to access them you need to be root, press Alt F2 and type "gksu nautilus".

---

### Post by your_average_bro on 2011-03-06
Let me clarify.
I have GRUB2 installed on my USB stick and it boots to Ubuntu 10.10 via the loopback feature, so basically, all it is is booting from an Ubuntu .iso that is on the stick; its not 'installed' onto the stick.

I would like to keep it this way; I'm not trying to install Ubuntu on my flash drive, I'd like to keep the ISO loopback option, as it is nice and clean.

What I'm trying to do is access the flash drive while running the Ubuntu 10 off of the flash drive.
There are no hints of the flash drive in fdisk, and the ^ /cdrom method doesnt show the root of the actual flash drive.

Anybody?

[B]EDIT: CS Cameron your the fukcing man!!
[/B]Your suggestion worked, to an extent.
gksu nautilus brings me to /root, where I just pressed the back button.
The root of my flash drive was located in /isodevice, not /cdrom

Thanks dude, your a lifesaver.

[B]EDIT2: gksu nautilus is not neccesary.
[/B]You can go right to File System/isodevice from 'Places'

---

