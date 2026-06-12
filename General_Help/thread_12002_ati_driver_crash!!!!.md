---
title: "ati driver crash!!!!"
date: 2005-01-21
forum: General Help
---

### Post by T31 on 2005-01-21
I was following the steps of this how to in the ubuntu wiki [http://www.ubuntulinux.org/wiki/BinaryDriverHowto](http://www.ubuntulinux.org/wiki/BinaryDriverHowto)

and when i try to change the resolution i get this message
______________________________________________
The X Server does not support the XRandR extension.  Runtime resolution changes to the display size are not available.
______________________________________________

i have a 14" screen and work in 1280x1024 is not exactly the best option, everything is too "mini" and the refresh of my old screen is awful

please help!!! :cry:

note:ati 9600 SE

---

### Post by daniels on 2005-01-21
You'll have to edit /etc/X11/xorg.conf and remove all references to 1280x1024; the ATI driver does not let you change resolutions while it's running.

---

### Post by hubris on 2005-02-05
that folder contains no xorg.conf

anyone know why it ain't there?

---

### Post by whatever on 2005-02-06
probably you use XFree and not Xorg, so you should edit /etc/X11/XF86Config-4
the driver will always use the highest resolution listed there in the "Screen" section

---

