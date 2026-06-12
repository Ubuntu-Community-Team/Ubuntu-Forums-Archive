---
title: "Resolution Dropped to 640x480 After Rebooted"
date: 2011-08-15
forum: General Help
---

### Post by W.J.C on 2011-08-15
I was using the 64-bit version of Ubuntu 11.04, with NVIDIA driver 280.11 and GNOME Shell. My computer rebooted suddenly (it usually occurs if I keeps it turns on for more than 1 day) and my screen resolution ended up 640x480 (originally 1680x1200) while my System Settings-Display stated that my display is "Unknown". I tried to install the new 280.13 driver but the problem remains. Can someone tells me how to recover my resolution? I really can't work with resolution like this :(

---

### Post by wojox on 2011-08-15
You need to set the res as root.

```
gksudo nvidia-settings
```

---

### Post by W.J.C on 2011-08-15
Tried it, still doesn't work :(
The resolution option got only Auto, 640x480 and 320x240. I clicked Detect Displays but it doesn't works too.

---

### Post by Grenage on 2011-08-16
> **W.J.C said:**
> Tried it, still doesn't work :(
The resolution option got only Auto, 640x480 and 320x240. I clicked Detect Displays but it doesn't works too.

You can either use xrandr, or a custom xorg.conf; since nvidia-settings uses xorg.conf anyway, you might as well use that.  If you can post your monitor make and model, I'll jot you a quick config.

---

### Post by W.J.C on 2011-08-16
I'm using BenQ T221W. Thank you very much :)

---

### Post by Grenage on 2011-08-16
Ah, BenQ - one of the few manufacturers that list useful model specs on their website.  The specs say it has a native res of 1680x1050, so is it possible you're mistaken about 1600x1200?  If so, try the stuff below; if not, post back.

```
Section "Monitor"
	Identifier "Monitor0"
	VendorName "BenQ"
	ModelName "T221W"
	HorizSync 30 - 82
	VertRefresh 56 - 76
EndSection

Section "Device"
	Identifier "Device0"
	Driver "nvidia"
	VendorName "Nvidia GTS250"
EndSection

Section "Screen"
	Identifier "Screen0"
	Device "Device0"
	Monitor "Monitor0"
	SubSection "Display"
		Depth 24
		Modes "1680x1050"
	EndSubSection
EndSection
```

If that does not work, add a modeline so it looks like this:

```
Section "Monitor"
	Identifier "Monitor0"
	VendorName "BenQ"
	ModelName "T221W"
	HorizSync 30 - 82
	VertRefresh 56 - 76
Modeline "1680x1050_60.00"  146.25  1680 1784 1960 2240  1050 1053 1059 1089 -hsync +vsync
EndSection

Section "Device"
	Identifier "Device0"
	Driver "nvidia"
	VendorName "Nvidia GTS250"
EndSection

Section "Screen"
	Identifier "Screen0"
	Device "Device0"
	Monitor "Monitor0"
	SubSection "Display"
		Depth 24
		Modes "1680x1050"
	EndSubSection
EndSection
```

---

### Post by Grenage on 2011-08-16
I just realised that I assumed you'd know how to edit the file. *slaps hand*.

from a terminal, type:

```
gksu gedit /etc/X11/xorg.conf
```

Remove what's there, and add the config I gave you.  If you develop problems and can't log in graphically, deleting the config will allow the normal boot to occur:

```
sudo rm /etc/X11/xorg.conf
```

---

### Post by W.J.C on 2011-08-16
Thank you very much :)
The resolution is fine now but the screen has lot of white spots sparkling. Why my system suddenly can't automatically detects my monitor anymore?

Update: It works fine now after I changed the VertRefresh from 56 - 76 to 56 - 60.

---

### Post by Grenage on 2011-08-16
Good work!  The white spots sound a bit odd, especially since the ranges are from BenQ's site.  Not that it matters, since you'll only be using 60, and the range is only for possibilities - they'll rarely be used, if ever.

For some reason, Ubuntu isn't getting the EDID data from your monitor.  This could be down to a bad cable, a splitter, a driver glitch, et cetera.  It is rather common, and for some reason Ubuntu still has no option for forcing a particular resolution.

---

