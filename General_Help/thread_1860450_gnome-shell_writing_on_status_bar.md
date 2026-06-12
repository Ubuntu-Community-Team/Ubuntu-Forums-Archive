---
title: "gnome-shell writing on status bar?"
date: 2011-10-14
forum: General Help
---

### Post by Foxheadz on 2011-10-14
So i just updated to 11.10, really excited that gnome-shell is easily useable as it caused me lots of trouble. So i got it up and running but on the status bar (whatever the bar at the top is called) has writing on it like "File, Edit, Help" its very faint but quite annoying... anyone know how to fix this? Attached is a screen shot.

---

### Post by cb951303 on 2011-10-15
> **Foxheadz said:**
> So i just updated to 11.10, really excited that gnome-shell is easily useable as it caused me lots of trouble. So i got it up and running but on the status bar (whatever the bar at the top is called) has writing on it like "File, Edit, Help" its very faint but quite annoying... anyone know how to fix this? Attached is a screen shot.

I have exactly the same problem. You tagged the thread as SOLVED. Would you care to share the solution?

---

### Post by alex2112 on 2011-10-15
Same problem here. If there is a solution please share. Thanks.

---

### Post by Delnar_Ersike on 2011-10-15
I found the solution in some post I can't seem to find. You need to remove three packages via apt-get or synaptic: appmenu-gtk, appmenu-gtk3, and appmenu-qt. Reboot and the problem's solved! If you want the menu back again, just install those three packages, reboot, and you're done.

Removal code:
```
sudo apt-get remove appmenu-gtk appmenu-gtk3 appmenu-qt
```
Reinstall code:
```
sudo apt-get install appmenu-gtk appmenu-gtk3 appmenu-qt
```

---

### Post by Foxheadz on 2011-10-15
Ah well if you don't use icons on your desktop you can just stop nautilus from handling the desktop, you can do that from gnome-tweak-tool under the desktop tab. If you do use icons on your desktop you can still fix it by removing the Global menu (Appmenu) but that will get rid of the menu in Unity, but if you no longer use Unity it shouldn't be a problem

---

