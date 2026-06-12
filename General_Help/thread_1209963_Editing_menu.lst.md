---
title: "Editing menu.lst"
date: 2009-07-10
forum: General Help
---

### Post by Feelin_froggy8877 on 2009-07-10
First off, hope it's not too big a deal this has nothing to do with ubuntu. But since its more of a grub question and its being added to my ubuntu's menu.lst it would be ok :) I'm doing a full install with puppypc and having a boot problem ((disk does not exist). I'm guessing it has to do with the extended partition on the disk its installed to (not sure) The frugal went fine on my primary hdd 

(frugal install) On (sda1)

title Puppy Linux 413 frugal
rootnoverify (hd0,0)
kernel /puppy413/vmlinuz pmedia=atahd psubdir=puppy413 nosmp
initrd /puppy413/initrd.gz

(full install) (sdb6)
title Puppy Linux 413 full install
root (hd1,5)
kernel /boot/vmlinuz root=/dev/sdb6 pmedia=atahd nosmp

Thats on my second hdd (sdb) it is partitioned like this...

/dev/sdb1 ext3
dev/sdb2 (extended)

/dev/sdb6 ext3 (where puppypc full install is)
/dev/sdb5 fat32
/dev/sdb7 swap

Any help would be appreciated. thanx

---

### Post by master_kernel on 2009-07-10
Could you describe your problem?

---

### Post by Feelin_froggy8877 on 2009-07-10
I'm getting (selected disk does not exist) when trying to boot the full install on sdb6. Sry, guess I did not make that very clear.

---

### Post by Jebtrix on 2009-07-10
/dev/sdb1 ext3
dev/sdb2 (extended)

/dev/sdb6 ext3 (where puppypc full install is) (You sure /boot is here?)
/dev/sdb5 fat32
/dev/sdb7 swap

---

### Post by Jebtrix on 2009-07-10
I never tried booting from an extended partition but I don't think grub view it this way:

root (hd1,5) = /dev/sdb6

Logically sdb6 would be 5, but I doubt grub sees it like that

I would try hd1,2 or hd1,3

---

### Post by egalvan on 2009-07-10
Here is all my Puppy related GRUB stuff..

```
## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd0,4)
.
.
.
# This is a divider,
# added to separate the menu items below from the Debian
# ones above.
title		Other *nix OS's:
root

#   original puppy frugal install, no longer used, does not exist
# title		Puppy Linux 4.00, no longer used, does not exist
# rootnoverify	(hd0,5)
# kernel	/vmlinuz root=/dev/ram0 pmedia=idehd
# initrd	/initrd.gz

#   previous puppy frugal install, using folder, no longer used, still exists
#title		Puppy 4.11
#rootnoverify	(hd0,5)
#kernel		/puppy_411/vmlinuz root=/dev/ram0 pmedia=idehd psubdir=puppy_411
## pfix=ram	if used, will not load "save files"
#initrd		/puppy_411/initrd.gz

#   current puppy frugal install, using folder
title		Puppy 4.12, using 411 "save files"
rootnoverify	(hd0,5)
kernel		/puppy_412/vmlinuz root=/dev/ram0 pmedia=idehd psubdir=puppy_412
# pfix=ram	if used, will not load "save files"
initrd		/puppy_412/initrd.gz
```

This is on a single drive system. Works great.
I have it installed on a dual drive system, with XP & Hardy on first drive, and Puppy and Jaunty on the second.

And here is a screenshot of my single drive layout...
note one primary for XP, and all things Linuxy are on one extended partitiob.
It's out on loan, so I cannot get copies of the menu.lst

But it works just fine. and has been for over a year.

And here is a screenshot of my single drive layout...
note one primary partition for XP, and all things Linuxy are on one extended partition.

**dev/sda6** is equal to **(hd0,5)**

---

### Post by egalvan on 2009-07-10
> **Jebtrix said:**
> I never tried booting from an extended partition but I don't think grub view it this way:

root (hd1,5) = /dev/sdb6

Logically sdb6 would be 5, but I doubt grub sees it like that

I would try hd1,2 or hd1,3

On my system...

#rootnoverify	(hd[COLOR="Red"]0[/COLOR],5)  =  sd[COLOR="Red"]a[/COLOR]6

so one can say that

#rootnoverify	(hd[COLOR="Red"]1[/COLOR],5)  =  sd[COLOR="Red"]b[/COLOR]6


I use gparted to see exactly what the partitions are called.
gparted and GRUB have the same naming convetions.

I also use LABEL to make it easier to distinguish things.

---

### Post by Feelin_froggy8877 on 2009-07-12
Well, I ended up having to reinstall everything due to a unwanted downgrade...ugh, but thats besides the point. Ubuntu added the puppy install to the menu.lst automaticly. And as far as I can tell it's pretty much the same, as far as where it's located. Thanx for all the replies though :)

Ubuntu's generated entry...

title		unknown Linux distribution (on /dev/sdb6)
root		(hd1,5)
kernel		/boot/vmlinuz root=/dev/sdb6 
savedefault
boot

Puppy's generated entry at puppy install...

title Puppy Linux 413 full install
root (hd1,5)
kernel /boot/vmlinuz root=/dev/sdb6 pmedia=atahd nosmp

---

