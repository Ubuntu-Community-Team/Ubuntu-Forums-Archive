---
title: "stuck after 10.04 upgrade, where from here??"
date: 2010-05-26
forum: General Help
---

### Post by jonesa3 on 2010-05-26
Hello!  I'm pretty frustrated here, and can't quite find an answer to my issue:

I finally gave in tonight and upgraded to 10.04.  When it went to restart, it wouldn't boot back in.  I got the error:

Gave up waiting for root device. Common problems:
-Boot args (cat /proc/cmdline)
- Check rootdelay= (did the system wait long enough?)
- Check root= (did the system wait for the right device?)
- Missing modules (cat /proc/modules; ls /dev)
ALERT! /dev/disk/by-uuid/6cb7dd44-88ea-4345-a661-4bbd**** does not exist. Dropping to a shell!!

BusyBox v1.13.3 (Ubuntu 1:1.13.3-1ubuntu11) built in shell (ash)

(initramfs)


Ok, so when I was upgrading, I chose to "keep the existing version" of the boot file or something (forget the wording, but I get the impression it's the menu.lst).  This may affect things.

Ok, so I'm staring at the (initramfs) line on the screen.  Where should I go from here?  I'm working with a normal ubuntu desktop install on a toshiba netbook (worked just fine with 9.10).

THANKS SO MUCH IN ADVANCE.  You have no idea how frustrated I am, considering I have important notes on this machine!

---

### Post by freddiespagheti on 2010-05-26
Not exactly a solution to your problem, but you could try grabbing a live-cd, start it up, copy your important files onto a usb drive, and then do a clean install.

---

### Post by jonesa3 on 2010-05-26
Yeah, I'll be keeping this as my plan of last resort.  The thing keeping me from doing this is that I think the install and all my stuff is still fine, but the bootloader just can't get a hold of the right part of the drive to begin.  I just don't know how to direct it to the right part.

Thanks for the quick reply though!

---

### Post by freddiespagheti on 2010-05-26
Silly me, I should have said try Super Grub Disk. It usually solves my boot problems.

---

### Post by jonesa3 on 2010-05-26
What's this?

---

### Post by freddiespagheti on 2010-05-26
[http://www.supergrubdisk.org/](http://www.supergrubdisk.org/)

It's a live cd (or USB, whatever you prefer). It uses a text-based interface and has the ability to fix Grub and boot to the OSes on your computer. It also walks you through the whole process but I'm sure you can also find tutorials online if the included instructions aren't clear. Just be sure to choose the option that says 'with help'.

---

