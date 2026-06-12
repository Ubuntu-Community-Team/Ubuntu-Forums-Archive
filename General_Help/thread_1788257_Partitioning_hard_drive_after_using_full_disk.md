---
title: "Partitioning hard drive after using full disk"
date: 2011-06-22
forum: General Help
---

### Post by gillbilliee on 2011-06-22
Hi i was hopeing to create a partition seperate from my home directory out of it. i have a 500 gig hard drive and i wish to create a 70 gig partition on it on install i used entire disk is there any way to make a partition after this for i do not want to reinstall. Any help on this would be much apriciated.

many thanks 

Gillbilliee

---

### Post by nothingspecial on 2011-06-22
First, back up all our stuff to something external then unplug it.

Then boot up the live cd and find the partition editor in the menus.

Everything should go ok, but things can go wrong.

---

### Post by dino99 on 2011-06-22
you can use parted (gparted for gnome gui) at any time to tune your hdd(s) (simply take care of the partitions in use) and only apply on unmounted partition

---

### Post by gnicko on 2011-06-22
Check this out. It may make things much easier for you:
[http://gparted.sourceforge.net/index.php]("http://gparted.sourceforge.net/index.php")

Download the disk image then boot from the CD. This will allow you to work with your installed disk(s) without them being mounted, etc. From the menu, start up gPartEd and go from there. It should be fairly straight-forward. Check back if you need more help.

This might be useful too: 
[http://gparted-forum.surf4.info/index.php]("http://gparted-forum.surf4.info/index.php")

...also, be sure to back up anything you can't afford to lose.

---

