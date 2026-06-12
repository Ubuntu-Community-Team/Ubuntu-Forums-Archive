---
title: "Which graphics driver is loaded?"
date: 2010-01-16
forum: General Help
---

### Post by narr on 2010-01-16
Well, I'd like to know which graphics driver Xorg is currently using. I suppose that it is possible to read that out of Xorg.0.log - I have just no idea where in this file. For example, my Xorg.0.log (Xserver started without a xorg.conf file): [http://paste.ubuntu.com/357623/](http://paste.ubuntu.com/357623/)

So, in which line(s) does this information hide? :)

---

### Post by Locutus_of_Borg on 2010-01-16
looks like you are using:

```
(II) Loading /usr/lib/xorg/modules/drivers//radeon_drv.so
(II) Module radeon: vendor="X.Org Foundation"
	compiled for 1.6.4, module version = 6.12.99
	Module class: X.Org Video Driver
	ABI class: X.Org Video Driver, version 5.0
```

so the radeon driver

---

### Post by narr on 2010-01-16
But it also says: 
```
(II) LoadModule: "vesa"
(II) Loading /usr/lib/xorg/modules/drivers//vesa_drv.so
(II) Module vesa: vendor="X.Org Foundation"
	compiled for 1.6.3, module version = 2.2.1
	Module class: X.Org Video Driver
	ABI class: X.Org Video Driver, version 5.0
(II) Loading /usr/lib/xorg/modules/drivers//ati_drv.so
(II) Module ati: vendor="X.Org Foundation"
	compiled for 1.6.4, module version = 6.12.99
	Module class: X.Org Video Driver
	ABI class: X.Org Video Driver, version 5.0

```
:confused:

---

### Post by Locutus_of_Borg on 2010-01-16
yes, but if you look down from about line 477 onwards, you see the radeon driver is the one actually being used, it is the driver detecting the card, assigning video ram, setting resolution, etc.

---

### Post by narr on 2010-01-16
Allright, thanks for your answer :)

---

### Post by fancypiper on 2010-01-16
The command **lsmod** will list the modules loaded, one of which should be your video driver.

---

### Post by Locutus_of_Borg on 2010-01-16
lsmod lists loaded kernel modules

the graphics driver is a component of X

X is not part of the kernel

there is of course graphics diver support in the kernel, but you will still need the Xorg driver, also, if you build a monolithic kernel, then there will not be modules to be listed

---

