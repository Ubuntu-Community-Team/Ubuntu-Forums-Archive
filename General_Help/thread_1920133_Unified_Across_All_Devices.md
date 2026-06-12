---
title: "Unified Across All Devices"
date: 2012-02-04
forum: General Help
---

### Post by Kreeyon on 2012-02-04
I have only recently come back to using Ubuntu and have spent a great deal of time customising various aspects of the desktop, from changing the fonts changing the sizes of the icons installing applications running various scripts to create various effects and extra functionality in order to get the experience that I need from Ubuntu.  

The issue that I have now is that I would like to install Ubuntu on my laptop also, but don't want to have to spend the next few hours or days customising all over again in order to get the same experience I have already set on my desktop.

Is is possible to save your Ubuntu setup on one device and then have it installed to a new device?

---

### Post by Habitual on 2012-02-04
I'd logout of the desktop and go to a console using Ctrl+Alt+F1
and log in as yourself. The goal here is to NOT have any DE environment loaded.

from where it is customized:
```
cp -pr ~/.gconf ~/.config /media/my_usb_device
```

to where it needs to be customized:
```
cp -pr /media/my_usb_device/.config /media/my_usb_device/.gconf ~
```

This will 'import' more than you need and may cause unexpected behavior, but the visuals/settings/customs should be fine.

This process assumes gnome* and is dated by about 2 years.
Others may have more elegant solutions.

HTH.

---

### Post by Kreeyon on 2012-02-04
Would just cloning the Ubuntu partition and copying it to the new laptop work?

---

