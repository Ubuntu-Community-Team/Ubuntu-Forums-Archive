---
title: "&quot;Could not find kernel image: linux&quot;"
date: 2010-02-12
forum: General Help
---

### Post by CycloneJoker on 2010-02-12
I decided today to try Xubuntu on my netbook.  I downloaded an ISO of it, formatted my old 2GB Sandisk Cruzer Micro, and used Unetbootin to copy all the stuff onto the drive.  Then, as I went to boot, I got the following message:

```
EXTLINUX 3.63 Debian-2008-07-15 EBIOS Copyright (C) 1994-2008 H. Peter Anvin
Could not find kernel image: linux
boot:

```

Of course with flashing cursor after "boot:".  So I tried rewriting with Unetbootin, and then even tried writing an ISO of Kubuntu to the flash drive.  Each and every time, I get the same message.  What's going wrong here?

---

### Post by CycloneJoker on 2010-02-12
Anybody?  Can we please not let this be like almost every other question I ask on here, with a bunch of people looking but nobody bothering to say anything?

---

### Post by CycloneJoker on 2010-02-12
Okay, seriously, what is it about this question that is so impossible for someone to answer?

---

### Post by Iowan on 2010-02-12
OK, guilty - I looked. "Could not find kernel image: linux" doesn't mention Xubuntu (my Xubuntu machine died before I really got to use it). I've never used Unetbootin or tried a flash drive boot - so I didn't see that a post would provide any useful information - but at least you now have a reply...

---

### Post by ironclaw on 2010-02-12
You can try formatting as vfat instead of ext3/4 for unetbootin. Or try using usb-creator-gtk (i.e., USB Startup Disk Creator in Ubuntu) instead of unetbootin.

---

### Post by SteveF48 on 2010-02-24
I'm going crazy with the same error.
I've formatted the usb drive as FAT16, created it with the built-in System Administration Option (USB Startup Disk Creator) and tried the pendrivelinux program. Most times the laptop says the same thing, though once it said remove disk and press any key to reboot (I did as that message suggested - nothing happened!). 
One of the posts related to this question suggests editing syslinux.cfg, or text.cfg. Ubuntu says that these are programs and won't open them.
I've lost a month of photographs, because I accidentally repartitioned the wrong usb drive (sdb instead of stg - why can't gparted use the disk name instead of ancient symbols?)
It appears that booting from usb pen drives is an arcane art, rather than computer science. Other posts imply that some types of drive just don't work.
If anyone can come up with a solution in the next few hours I would be very grateful.
Thanks for reading this.

---

### Post by IzByFl on 2012-03-29
[http://www.pendrivelinux.com/error-could-not-find-kernel-image-linux/](http://www.pendrivelinux.com/error-could-not-find-kernel-image-linux/)

---

### Post by IzByFl on 2012-03-29
i just found a solution that worked for me.
just type "live"  (boot:live)

---

