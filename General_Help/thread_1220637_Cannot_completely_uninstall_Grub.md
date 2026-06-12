---
title: "Cannot completely uninstall Grub"
date: 2009-07-23
forum: General Help
---

### Post by hotnikkelz on 2009-07-23
Hi guys, I messed up when i was installing ubuntu. I wanted to dual boot windows xp 64 bit.

I'm now stuck with Ubuntu and XP 64 bit when i startup, and i already uninstalled Ubuntu, i see no partitions or anything, so hence i i think it's an issue with the mbr.

I downloaded MBRfix to repair my MBR and followed the instructions, but it simply doesn't work, ubuntu is ever present when i restart. What do i do from here? i don't have a windows XP installation CD on hand so i can't go into recovery console and do the fixmbr from there. 

It's quite a bit annoying that this mbrfix works for everyone else...BUT me :'(

---

### Post by codyxx on 2009-07-23
Boot into Ubuntu:

From there, go into terminal and type this command:

```
gksudo gedit /boot/grub/menu.lst
```

From there, there is a little guide in that file as to how you would edit the GRUB menu to allow switching between Windows and Ubuntu.

PM me if you have any more problems. 

Godspeed,
Cody

---

### Post by x33a on 2009-07-23
if yo can boot into windows, download and give supergrubdisk a try.

[http://www.supergrubdisk.org/](http://www.supergrubdisk.org/)

---

### Post by hotnikkelz on 2009-07-23
codyxx:
Ubuntu is already uninstallled from my system, however i did follow the instructiosn you gave, i went into Ubuntu via the cd method. (try ubuntu without changing anything option)
When i typed that command in terminal, it gives me a blank page in a document called menu.1st :/

x33a
I don't know what's up with that program, it did nothing for me.  I am  probably not understanding it at all.

---

### Post by x33a on 2009-07-23
hi download this file:

[http://prdownload.berlios.de/supergrub/super_grub_disk_0.9797.iso](http://prdownload.berlios.de/supergrub/super_grub_disk_0.9797.iso)

it's a bootable iso. burn it to a cd at low speed.

configure your bios to boot from cd first, then boot into this disc.

for a tutorial on this, take a look here:

[http://www.linuxplanet.com/linuxplanet/tutorials/6572/1/](http://www.linuxplanet.com/linuxplanet/tutorials/6572/1/)

---

### Post by hotnikkelz on 2009-07-24
Geez, i find it rather inconvenient to burn a 4MB file on a DVD, is there another option? If not then I guess i'll have no choice but to do it. Thanks again.

---

### Post by stevie1989 on 2009-07-24
> **x33a said:**
> if yo can boot into windows, download and give supergrubdisk a try.

[http://www.supergrubdisk.org/](http://www.supergrubdisk.org/)
Or if in Kubutnu, Kgrubeditor. Amazing, three clicks l removed the duplicates from upgrading 8 to 9, added a background and renamed a boot option :)

---

