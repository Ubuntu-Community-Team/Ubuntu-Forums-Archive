---
title: "Completely disable nVidia drivers"
date: 2006-06-27
forum: General Help
---

### Post by bforbes on 2006-06-27
I installed the nVidia graphics drivers, and I know I can change "nvidia" back to "nv" in xorg.conf to disable them, but then programs like glxgears will not run at all. How can I run glxgears and similar programs like I used to, before I installed the drivers? I'd prefer not to have to uninstall the drivers completely.

EDIT: The message I get using the nv driver is:
```

Xlib:  extension "GLX" missing on display ":0.0".

```

---

### Post by woedend on 2006-06-27
sudo /etc/X11/xorg.conf

In the beginning section, make sure you have 
Load      "glx"

just curious - why do you not like the nvidia drivers?

---

### Post by bforbes on 2006-06-27
My graphics card has issues, it sometimes makes the computer stall. I try not to have the drivers enabled when I'm doing hard-drive intensive operations like BitTorrent, to prevent data corruption.

I do have glx there, it must be something else. Maybe I should compare everything in /etc before and after uninstalling the drivers?

---

### Post by dragonflyseven on 2006-11-24
> **woedend said:**
> sudo /etc/X11/xorg.conf

Shouldnt that be sudo nano /etc/X11/xorg.conf

I also want to disable my Nvidia card/drivers. When I change the driver to nv, the screen resolution switches to 800*600 so I have to pan with the mouse to see the whole screen. Anyone have any ideas?

---

