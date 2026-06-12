---
title: "livecd w/ /home on a flash drive?"
date: 2010-11-15
forum: General Help
---

### Post by i.r.id10t on 2010-11-15
Building a custom livecd for a dev environment for programming students to use.  I'd like to have everything run off CD, but I'd like to have /home be mounted from a flash drive.

While the instructions at [https://help.ubuntu.com/community/LiveCDCustomization](https://help.ubuntu.com/community/LiveCDCustomization) are working great for creating the CD (been using them for years) I can't get a flash drive mounted for the livecd user to use as /home/ubuntu

So.. at what point in the boot process for the CD can I do this? Which file to edit?  I tried using rc.local and touching a file in /tmp but it does not show... so getting /home mounted there won't do it.

Ideas?

Thanks

---

### Post by Hippytaff on 2010-11-15
You can partition a liveUSB, so you can boot from usb and have a seperate /home partition on the USB...I know this is not what you are asking, but it's a alternative to what you are trying to do, if it turn out it can't be done :-)

---

### Post by i.r.id10t on 2010-11-15
The issue is that most flash drives are too slow when it comes to i/o ... if you do an install to flash, you'll notice that like firefox locks up and "grey screens" when there is a lot of I/O going on... I'd like the OS to run from CD/DVD and just store ~/ stuff on the flash drive.

---

### Post by TNT1 on 2010-11-15
It can be done, I think, cause I have seen posts advising against have /home on a usb hdd. Apparently it will be super slow.

---

### Post by i.r.id10t on 2010-11-15
Solved.  Pass "persistent" as a boot arg to the standard live cd and it will Just Work if you have a flash drive w/ an ext2/3/4 partition that has the label "casper-rw"

Still interested in "a different way" to do it

---

### Post by C.S.Cameron on 2010-11-16
I'm glad to know that this is still working with Live CD's, for a while it was hard to get working consistently.
Besides for the casper-rw partition you can also make a second partition named home-rw that will only hold a persistent home folder.

---

