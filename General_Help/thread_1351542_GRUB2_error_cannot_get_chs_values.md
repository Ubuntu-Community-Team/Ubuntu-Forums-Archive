---
title: "GRUB2 error cannot get c/h/s values"
date: 2009-12-10
forum: General Help
---

### Post by andyvr4 on 2009-12-10
Hi,

I just got a new msi p55-gd80 motherboard and went to install ubuntu 9.10 to the computer.  The installation went great with no errors at all, but when I went to boot the new install I'm getting the error message "cannot get c/h/s values".  Do you guys have any idea why I'm getting this error message and what I can do to fix it?

Thanks,
Andy

---

### Post by andyvr4 on 2009-12-11
Anybody got any ideas?

Just to update I tried ubuntu 9.04 and everything went smoothly.  It appears the issue is related to grub2 however I have no idea what the issue is!

---

### Post by cozmicharlie on 2010-06-10
It is a known bug in Grub2 ([http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=565706](http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=565706)).  Apparently from what I have read it relates to certain Motherboards that treat usb devices as floppies.  Not sure I understand it and I have not read a good fix.  Some report upgrading to Grub 1.98 works but it didn't for me.  A few options are available but it seems there is no one workaround that works for everyone - you just have to try some and hope one of them works for you.  One full proof way to be able to boot into your various OS (if you dual boot) is to use the Super Grub Disk ([http://www.supergrubdisk.org/](http://www.supergrubdisk.org/)).  A very handy tool to keep around.  Just download the iso file, burn to a cd, load it in your cd/dvd player on your computer and boot to the cd.  You should see a menu with numerous options that let you boot into your system.

Another option is to try and set your devices in the bios to automatic (any hard drives, usb or floppies).  Others report that disabling the floppy in bios helps.  try this if you are comfortable working in your bios.

Another option is when you get the prompt grub rescue> type one of the following:

grub rescue > insmod linux

or in sequence write:
grub rescue > insmod normal
grub rescue > normal

One of these options should work.  Hopefully they will fix this bug soon.

---

