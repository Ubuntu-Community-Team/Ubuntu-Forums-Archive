---
title: "grub kills dvd drive"
date: 2006-03-19
forum: General Help
---

### Post by jiggling_john on 2006-03-19
I have a rather bizarre problem...

My dvd drive is a liteon dvd writer (not sure off the top of my head which model). I installed kubuntu on hdd (secondary slave) I have the dvd drive as secondary master, and two ntfs drives as primary master and slave.

Grub is installed to hda (primary master). The problem is this, my dvd drive works up until the point where grub loads itself. I can boot from my dvd drive, if i fdisk /mbr and only have windows booting - it works. But grub kills it dead - i cant even get it to open the drawer, it turns it off.

I've tried reinstalling grub, i've tried another drive in there and that seems to work (sony cd writer). Why does grub want to turn my liteon off??! any ideas?

I've checked all cables and jumpers and there's no problems there...

---

### Post by jiggling_john on 2006-03-20
well, i fixed it myself. Installed lilo...

---

