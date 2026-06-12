---
title: "brasero can't see dvd rw (or maybe entire drive?)"
date: 2009-10-26
forum: General Help
---

### Post by pythonscript on 2009-10-26
I just installed ubuntu 9.1, and it doesn't see my DVD drive! I inserted a blank DVD-RW, and it won't show up (on the desktop, automatically, anything) so when I try to burn an iso to that DVD using brasero, it just says "No recordable CD or DVD found" but I know the disk is there... *please help me!* I need to be able to burn disks pretty urgently!

EDIT:  This appears to be only in brasero and the rest of gnome... because gnomebaker is burning a disk right now! However, last time I burned a disk, it wouldn't boot in my computer (it's a windows 7 installation disk) so I thought if I burned it slower, it'd make a difference, but gnomebaker gives an error of "couldn't change burn speed" and just keeps on burning. Any help here!?

---

### Post by fancypiper on 2009-10-26
dupe

---

### Post by fancypiper on 2009-10-26
Select the burn speed **before** starting your burn!

Try this:

sudo apt-get install avidemux devede todiscgui tovidgui

---

### Post by pythonscript on 2009-10-26
> **fancypiper said:**
> Select the burn speed **before** starting your burn!

I did. I selected burn speed, then clicked Burn, and I got the error message. The burn did complete successfully, though, just at the higher speed. 

> **fancypiper said:**
> Try this:

sudo apt-get install avidemux devede todiscgui tovidgui

 I don't see how installing video editing software and movie-burning software will help. Could you elaborate on this more before I start dumping large packages onto my system? Thanks!

---

### Post by fancypiper on 2009-10-26
I thought it might catch a missing dependancy.

I would try removing and reinstalling brasero.  If that doesn't work, file a bugzilla report for brasero.

---

### Post by dannyc312 on 2009-12-07
I uninstalled and installed brasero - didnt work
downloaded and installed gnomebaker and bombs out just after adding files.

still not working??

---

