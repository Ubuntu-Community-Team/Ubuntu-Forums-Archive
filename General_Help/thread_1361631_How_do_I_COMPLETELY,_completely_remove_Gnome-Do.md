---
title: "How do I COMPLETELY, completely remove Gnome-Do?"
date: 2009-12-22
forum: General Help
---

### Post by martini1179 on 2009-12-22
I need to remove every last trace of Gnome-Do from my system. When I try to remove it via Synaptic and specify that I want to completer remove the three packages that comprise it (even going so far as to set "completely remove" for EACH package), and even after I delete all package files and reboot, upon redownloading and reinstalling it, Gnome-Do somehow retains all of my configuration settings: launchers, custom icons, custom icon size, docklets, etc. 

Since upgrading to Karmic x64 a few days ago, I'm having trouble with Gnome-Do and I think it's freezing my system, so I want to completely remove it so I can start fresh. How do I completely remove all of these custom settings?

---

### Post by philinux on 2009-12-22
Browse your home folder, ctrl h to see the hidden config files. There will be one for gnome-do

---

### Post by martini1179 on 2009-12-22
> **philinux said:**
> Browse your home folder, ctrl h to see the hidden config files. There will be one for gnome-do

That's the thing. There isn't a clearly-defined folder for Gnome-Do in the home directory for me. I have Do currently on my system, and yet there isn't a .Gnome-Do folder or anything similar. The closest thing I see is a few folders labeled .gnome, .gnome2, .gnome2_private, and .gnome_private -- and most of them are empty (hidden files are enabled).

---

### Post by bolucpap on 2009-12-22
You could create a new dummy user,then log on to it and use ```
 ls -lR > directorystructurebeforegnomedo.txt
``` at the terminal to take a snapshot before you run gnome-do, then after running gnome-do issue ```
ls -lR > directorystructureaftergnomedo.txt
``` again, and compare the two files to find out which ones Gnome-Do creates?

---

### Post by philinux on 2009-12-22
> **martini1179 said:**
> That's the thing. There isn't a clearly-defined folder for Gnome-Do in the home directory for me. I have Do currently on my system, and yet there isn't a .Gnome-Do folder or anything similar. The closest thing I see is a few folders labeled .gnome, .gnome2, .gnome2_private, and .gnome_private -- and most of them are empty (hidden files are enabled).

Stuff is in here.

```
/home/username/.local/share/gnome-do/
```

---

