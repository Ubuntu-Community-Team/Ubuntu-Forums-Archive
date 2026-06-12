---
title: "where to change X configuration options in Natty without xorg.conf"
date: 2011-05-24
forum: General Help
---

### Post by jt_04 on 2011-05-24
I need to add an option to my xorg.conf to enable "backing store", like this:

Section "Device"
  Identifier  "Miserable Old SVGA"
  Driver      "miserable"
  ** Option	"BackingStore"	"True"**
EndSection

But I don't have an xorg.conf file in Natty. There are several conf files in /usr/share/X11/xorg.conf.d/, but I'm not sure which one to add it too (I can't find the Device section in any of them).

I guess I don't even know if the "BackingStore" option is valid in the latext Xserver. 

any help would be greatly appreciated.

---

### Post by TeoBigusGeekus on 2011-05-24
Create one yourself and put your options in.

---

### Post by jt_04 on 2011-05-24
thanks very much, didn't realize it was that easy. I generated one with "sudo Xorg -configure" (needed to stop the xserver first), then added my option and put it in /etc/X11. Upon restarting X, analysis of the logfile shows that the BackingStore is enabled.

thanks!

---

