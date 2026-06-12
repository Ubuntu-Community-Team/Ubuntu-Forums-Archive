---
title: "Problems installing touchscreen on NC10 UNR"
date: 2009-12-27
forum: General Help
---

### Post by smartroad on 2009-12-27
Trying to install the drivers for the touchscreen. Having problems on the setup side, this is what I get:
```
(*) Linux driver installer for eGalax Touch controller 

(I) Check user permission: root, you are the supervisor.
(I) Begin to setup the eGalax Touch driver.
(I) Extract eGalax Touch driver archive to /usr/local/eGalaxTouch32.
(I) Create eGalaxTouch utility shortcut in /usr/bin.
(I) Create TKCal tool shortcut in /usr/bin.
(I) Check X window version: 1.6.x
(I) Copy X module: x16/egalax_drv.so to /usr/lib/xorg/modules/input.

(Q) Which interface controller do you use?
(I) [1] RS232 [2] PS/2 [3] USB : 3
(I) Using interface: USB
(I) Found a HID compliant touch controller.

(I) Removed eGalax Touch driver archive from /usr/local/eGalaxTouch32.
(I) Removed eGalaxTouch utility shortcut.
(I) Removed TKCal tool shortcut.
(I) Removed X module.
(E) No X configuration file found.

```

Don't understand why it says it has found the touch controller but the removes everything.

Using 9.10 UNR. Any help would be great as have the touchscreen working fine on Windows.

---

### Post by Breanainn on 2010-02-09
I'm having the exact same problem, did u figure out a solution?

does anyone know what the HID compliant touch controller is?

---

### Post by DrMaggi on 2010-03-03
Hey friends, this is because there is by default no Xorg.conf file.  To solve this, create one ;)  How, do this:  Now execute the following commands (best in a shell):  Stop the X server: #service gdm stop  Generate the Xfile: # Xorg -configure  Move it to the right destination # mv ~/xorg.conf.new /etc/X11/xorg.conf  Start gdm: #service gdm start   And last but not least, try again if the .setup.sh works --> hurray!  hope this helped & enjoy life

---

### Post by smartroad on 2010-05-09
That worked to get the driver installed thanks!

Now I just have a problem that every time I touch the screen the cursor goes to the upper left and messes with any windows that are there.

---

