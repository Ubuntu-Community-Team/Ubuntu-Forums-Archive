---
title: "Unable to increase resolution for remote desktop"
date: 2009-09-24
forum: General Help
---

### Post by jgb2185 on 2009-09-24
I am configuring a headless Ubuntu 9.04 server for my brother's classroom. As he has no Linux experience whatsoever, I have installed the gnome-desktop package atop the server install.

I have configured the machine to allow X to start up without a monitor by setting the video driver to "vesa"; this allows gdm and vino to run when the monitor is disconnected.

The current issue is that the remote desktop resolution is stuck at 640x480. I have tried several modifications to xorg.conf, without success. Attached is my current iteration.

The delivery date for this server is this Saturday 26 September, so I am under the gun. Any help gratefully accepted.

JGB

---

### Post by jgb2185 on 2009-09-24
I've boiled my **xorg.conf** down to a very simple version:

```

Section "Device"
	Identifier	"Configured Video Device"
	Driver		"vesa"
	Option		"UseFBDev"		"true"
	Option 		"NoDDCValue" 		 "True"
EndSection

Section "Monitor"
	Identifier	"Configured Monitor"
        HorizSync   30.0 - 95.0
        VertRefresh 50.0 - 160.0
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
EndSection

```

This still allows me to connect, but still shows me only a 640x480 screen.

Help, anyone?

JGB

---

### Post by Altadena on 2009-09-25
You can accomplish this with a 2-step process.

**1)** You need first to determine the modes supported by your video adapter when the monitor is connected to the system.

You can do that checking the resolution types in *Display Preferences *(System>Preferences>Display), or from Terminal with the following command:

```
xrandr
```**2)** Once you have the list of resolutions supported by your video card, you can edit /etc/X11/Xorg.conf and add the video modes that you want to use without the monitor in the *Screen *section of the configuration file.

This is the Xorg.conf that I use for my remote server without monitor.

```

Section "Monitor"
    Identifier     "Generic Monitor"
    HorizSync       27.0 - 96.0
    VertRefresh     50.0 - 160.0
    Option         "DPMS"
EndSection

Section "Device"
    Identifier     "Configured Video Device"
    # Option         "UseEdidFreqs" "False"
EndSection

Section "Screen"
    Identifier     "Default Screen"
    Device         "Configured Video Device"
    Monitor        "Generic Monitor"
    DefaultDepth    24
    SubSection     "Display"
        Depth       24
        Modes      "1152x864@85" "1152x864@75" "1152x864@70" "1024x768@85" "1024x768@75"
    EndSubSection
EndSection 

```Good luck,

-A

---

