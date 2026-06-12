---
title: "X Wont start :("
date: 2006-04-02
forum: General Help
---

### Post by GTar on 2006-04-02
Hey,

Just got a new computer and installing Ubuntu (used to work fine on the old PC).

Anyway, specs:
AMD Athlon 64 X2 4200+
nVidia 7900GT
Gigabyte K8N Pro-SLI
1GB Memory
...

Installation seems to go fine then, as ubuntu boots up it crashes to command line, saying there was an error with the X Window System. Incompatible hardware?

---

### Post by dcstar on 2006-04-02
[QUOTE=GTar]Hey,

Just got a new computer and installing Ubuntu (used to work fine on the old PC).

Anyway, specs:
AMD Athlon 64 X2 4200+
nVidia 7900GT
Gigabyte K8N Pro-SLI
1GB Memory
...

Installation seems to go fine then, as ubuntu boots up it crashes to command line, saying there was an error with the X Window System. Incompatible hardware?[/QUOTE]
Probably needs a different video driver, see my recent post on someone else's similar problem.

---

### Post by JoshHendo on 2006-04-02
Try installing the nvidia drivers:
[http://ubuntuos.com/2006/03/install-nvidia-drivers.html](http://ubuntuos.com/2006/03/install-nvidia-drivers.html) :)

---

### Post by zapcojake on 2006-04-02
sudo nano /etc/X11/xorg.conf.  There is a line which has the ddriver name in Quotes yours probably says "nv".  change it to "vesa" and it will get you going until you can install the driver from the howto or automatix.

Section "Device"
        Identifier      "ATI Technologies, Inc. Radeon Xpress 200 (RS480)"
        Driver          "vesa"
        BusID           "PCI:1:5:0"
Here's what mine looks like, on a clean install mine says ATI and doesn't work either. After you change the file press ctrl+o for write out and ctrl+x for exit.  Give the command startx at the terminal and you should be good to go.

---

