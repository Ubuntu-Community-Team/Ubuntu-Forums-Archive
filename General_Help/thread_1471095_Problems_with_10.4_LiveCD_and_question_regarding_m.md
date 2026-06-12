---
title: "Problems with 10.4 LiveCD and question regarding modifying the ISO image"
date: 2010-05-03
forum: General Help
---

### Post by Rubi1200 on 2010-05-03
Hi,
I have tried running the new version 10.4 at home as a LiveCD with no success. I then used a friend's computer and was able to get to the desktop with no problem.

The difference? Graphics card.
His computer: NVIDIA
My laptop: Intel i8xxx series.

This was posted on the release notes for 10.4:
[http://www.ubuntu.com/getubuntu/releasenotes/1004#Intel%208xx%20X%20freezes/crashes](http://www.ubuntu.com/getubuntu/releasenotes/1004#Intel%208xx%20X%20freezes/crashes)

This was also posted regarding such issues:
[https://wiki.ubuntu.com/X/Bugs/Lucidi8xxFreezes](https://wiki.ubuntu.com/X/Bugs/Lucidi8xxFreezes)

My question is twofold:
First, does anyone know of a way to boot the LiveCD, with boot parameters, so that I can get to the desktop and check out the new version?
Secondly, is it possible to modify /etc/X11/xorg.conf on the CD/ISO BEFORE booting?

Thanks in advance.

---

### Post by pcura on 2010-05-03
go to bios and change your boot sequence

cd/dvd first, 

floppy (if there is one) second

hard drive last

---

### Post by Rubi1200 on 2010-05-03
> go to bios and change your boot sequence

cd/dvd first, 

floppy (if there is one) second

hard drive last

The boot sequence is not the problem!
BIOS is already set to boot from the CD first.
Again, with all due respect, I repeat what I said above; this is a known bug.
I am looking for a workaround.

---

