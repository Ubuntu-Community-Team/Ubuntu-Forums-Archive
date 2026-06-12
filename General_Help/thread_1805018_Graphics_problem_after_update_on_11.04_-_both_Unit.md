---
title: "Graphics problem after update on 11.04 - both Unity and Gnome glitchy"
date: 2011-07-15
forum: General Help
---

### Post by apoorvumang on 2011-07-15
I have been having issues with graphics drivers recently 
([http://ubuntuforums.org/showthread.php?t=1801983](http://ubuntuforums.org/showthread.php?t=1801983) and [http://ubuntuforums.org/showthread.php?t=1802467](http://ubuntuforums.org/showthread.php?t=1802467)). 
Laptop specs:
```

Lenovo z570 laptop 
Intel i5 2410m processor 
Intel HD graphics (sandy bridge architecture)

```

Unity and Gnome work fine, however 3D performance is poor. I found that Fedora 15 and Ubuntu 11.10 alpha 2 has newer drivers, and installing them gave great graphics performance on my laptop.

So, when I saw some updates of xorg-intel and mesa in update manager today, I quickly installed those.

However, upon reboot, I found that both Unity and Gnome graphics are working very weird - white patches where a window used to be and was closed, menus not showing, windows not updating until I move them  - very clearly a graphics issue, most probably due to the update. However, 3D games are working great!

Has anyone else had problems with this update? And how do I undo the update? Synaptics isn't showing the packages installed during the update in it's history.

---

### Post by apoorvumang on 2011-07-15
I think I found the problem : xorg-edgers repository had been added by me recently, and the updates were from there.

---

