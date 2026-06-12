---
title: "Headless VNC won't work without monitor"
date: 2010-10-01
forum: General Help
---

### Post by gapjunk on 2010-10-01
I'm setting up a headless unit with Xubuntu (lucid), VirtualBox and Vino.  It works fine except that when I unplug the monitor and reboot I can't connect via VNC.  I can ssh in just fine.  If I try to plug in a monitor to see the display I get no signal.  My assumption is that Ubuntu detected no monitor and decided to ask me something or act differently.  This defeats my intent.

    -Gary

---

### Post by dcstar on 2010-10-02
> **gapjunk said:**
> I'm setting up a headless unit with Xubuntu (lucid), VirtualBox and Vino.  It works fine except that when I unplug the monitor and reboot I can't connect via VNC.  I can ssh in just fine.  If I try to plug in a monitor to see the display I get no signal.  My assumption is that Ubuntu detected no monitor and decided to ask me something or act differently.  This defeats my intent.


You may well have to create a custom xorg.conf file that does not use the default autodetection code.

---

### Post by spiky001 on 2010-10-02
Is there a setting in the bios to ignore no monitor

---

### Post by SteveDee on 2010-10-06
> **spiky001 said:**
> Is there a setting in the bios to ignore no monitor

No, this is not a BIOS problem. The X server needs to create an "image" that VNC can use, so you do need to add a custom section to xorg.conf (or for recent buntu versions, just a custom xorg.conf with the additional bits).

My headless print server (9.04) includes this in xorg.conf:-
```


Section "Device"
	Identifier	"Configured Video Device"
	Driver		"vesa"
EndSection


Section "Monitor"
	Identifier	"Configured Monitor"
	HorizSync 31.5-48.5
	VertRefresh 50-70
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
	DefaultDepth 24
	SubSection "Display"
	Depth 24
	Modes "800x600"
	EndSubSection
EndSection



```

---

