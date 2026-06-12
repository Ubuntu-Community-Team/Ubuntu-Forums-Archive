---
title: "Install Windows from Partition with Grub"
date: 2010-05-12
forum: General Help
---

### Post by Intrepid Ibex on 2010-05-12
So how can I (e.g. after using dd) boot to this dd'd Windows Installation partition with Grub?

I just want to do this as installing Windows from Hard Drive is much faster.

- Thanks from all the help already

**E:** The solution was [Unetbootin](http://unetbootin.sourceforge.net/). Did nothing special myself (defined the *.iso* path and the partition *(/dev/sda4)*), the app did all the work.

---

### Post by Intrepid Ibex on 2010-05-12
lolump

---

### Post by Intrepid Ibex on 2010-05-12
Well, okay, either I'm gonna do this with grub(2) with:
```
menuentry "For when hell freezes over..." {
	set root='(hd0,4)'
	chainloader +1 # I dun have the Windows's MBR override here so maybe chainloading won't work
}
```
or with [Unetbootin](http://unetbootin.sourceforge.net/).

---

### Post by john newbuntu on 2010-05-12
Try "sudo update-grub" from a terminal.  Also set the boot flag on that partition assuming this to be the only win install.

---

### Post by Intrepid Ibex on 2010-05-15
Uhhh... I never had a problem with updating (*/boot/grub/*)grub.cfg.. Also thanks but I already have set the boot flag. The problem is to just adjust the correct parameters (chainload or not), the filesystem (dd or ntfs) and stuff like that.

---

### Post by Intrepid Ibex on 2010-05-16
Okay, weee, [Unetbootin](http://unetbootin.sourceforge.net/) was the solution. I just added the *Win 7.iso*, defined the partition where I wanted it to (*/dev/sda4*) (*USB Drive* -> *Show All Drives (Use with care)* -> */dev/sda4*) and (of course) just pressed *OK*.

This (I don't know how but somehow) created a working MBR setup to boot from the partition I put the setup into (*/dev/sda4*).

What really took me by surprise was that about 2 years ago ago I had no luck with [Unetbootin](http://unetbootin.sourceforge.net/) what so ever (with either Ubuntu or Windows).

---

