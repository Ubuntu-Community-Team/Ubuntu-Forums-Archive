---
title: "boot problems after a new Desktop Environment"
date: 2010-06-13
forum: General Help
---

### Post by 2ndconfused1 on 2010-06-13
i was happily running ubuntu with gnome, when i realized i would need a faster desktop environment if i was going to use wine, so i got Xubuntu desktop environment from the software center.   now when i boot up (i am running a dual boot) i get 2 options for ubuntu, they look the same but if i were to click on the 2nd one i get a console and my keyboard doesn't respond.  i was wondering how to fix that (how to remove the 2nd option)
thx for your help

P.S. i wasn't sure whether to put this in Desktop environment or General Help sections

---

### Post by quixote on 2010-06-14
Grub is the program giving you those options, and how to fix it depends on which version of ubuntu you're running.  Lucid?  Karmic?  Or something earlier?

If it's Lucid, try opening a terminal (Accessories > Terminal) and typing ```
sudo update-grub
```Ideally, grub will then notice it has an invalid option in the list and get rid of it.

---

