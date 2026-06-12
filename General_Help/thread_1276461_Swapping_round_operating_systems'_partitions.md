---
title: "Swapping round operating systems' partitions?"
date: 2009-09-27
forum: General Help
---

### Post by djwkd on 2009-09-27
Hello (again),
I recently installed Crunchbang onto a drive that i had just installed (HDD,40GB), but Ubuntu only has about 10GB, and i use Ubuntu way more. 
So i want to put Ubuntu on my hard drive that has 40GB, and crunchbang on my 10GB partition (that is on another HDD).

Is this possible?

---

### Post by CatKiller on 2009-09-27
It's possible, but potentially tricky. You'll need either enough room on the larger drive to have them both on there or a third hard drive as an intermediate container.

---

### Post by SuperSonic4 on 2009-09-27
> **CatKiller said:**
> It's possible, but potentially tricky. You'll need either enough room on the larger drive to have them both on there or a third hard drive as an intermediate container.

+1 or any kind of storage as an intermediate container will do, just hdd is easier.

Backing up data externally and reinstalling both would be the easiest way but you can do it without reinstalling.

You would have to mess about with fstab and grub

---

### Post by djwkd on 2009-09-27
Yikes....Not so keen as soon as you said 'mess around with fstab and grub', particularly of 'sknife?' :P
(In other words, i've never heard of fstab.)

---

### Post by Shazaam on 2009-09-27
Four good tools to have if you want to tweak your pc...

1. Ubuntu livecd.

2. GParted stand-alone livecd-
[http://gparted.sourceforge.net/livecd.php](http://gparted.sourceforge.net/livecd.php)

3. Clonezilla-
[http://clonezilla.org/](http://clonezilla.org/)

4. SuperGrubDisk-
[http://www.supergrubdisk.org/](http://www.supergrubdisk.org/)

herman's website is great for dual-boot info-
[http://members.iinet.net/~herman546/index.html](http://members.iinet.net/~herman546/index.html)

---

### Post by CatKiller on 2009-09-28
> **djwkd said:**
> Yikes....Not so keen as soon as you said 'mess around with fstab and grub'

Relax. They're just text files.

[/etc/fstab]("https://help.ubuntu.com/community/Fstab") is the **f**ile**s**ystem **tab**le. It's the way that you tell your computer which partitions should be mounted where. All you need to do is make sure that the entries in there correspond to what you actually want to happen.

GRUB's [menu.lst]("https://help.ubuntu.com/community/GrubHowto") is just a list of options that say how your computer should be booted. If you've moved where the operating system is but haven't told your bootloader, it won't work.

The use of UUIDs largely mitigates against having to do this kind of thing, depending on exactly how you manage your repartitioning.

To be perfectly happy to mess around with partitions but scared to edit a couple of text files is a bit crazy. You'll be fine.

---

