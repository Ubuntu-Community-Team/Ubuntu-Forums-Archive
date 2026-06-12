---
title: "Can't change resolution higher than 1024x768"
date: 2011-05-18
forum: General Help
---

### Post by tommaat on 2011-05-18
I've just installed ubuntu 11.04 64-bit and can't select the native resolution of my screen (1280x1024).
I've tried both nvidia drivers (version 173 and the current version) but none seem to help me change the resolution.

Thanks in advance.

---

### Post by jasonab1 on 2011-05-19
You may need to edit your /etc/X11/xorg.conf file. 

What is happening is the system is unable to read the EDID info from your monitor. I have this same problem when my monitor is connected via my KVM switch. Plugged directly into the computer it works fine. I feel your pain.

xorg.conf does not come standard with ubuntu 11.04, you have to manually create it. 
[http://ubuntuforums.org/showthread.php?t=1336863](http://ubuntuforums.org/showthread.php?t=1336863)

Then you need to add a modeline for your monitor based on your screen size and desired resolution.
[http://www.grenage.com/xorg.html](http://www.grenage.com/xorg.html)

Hope that helps.

---

### Post by tommaat on 2011-05-19
Thanks jasonab1. I've followed all the steps.
However, after rebooting, the 'login screen' does not appear. I can only go into the terminal using (ctrl + alt + f1). (which is correctly displayed in 1280 x 1024)

Here is my xorg.conf

```
Section	"Monitor"
	Identifier	"Monitor0"
	VendorName	"Acer"
	ModelName	"AL1715"
	HorizSync	30 - 83
	VertRefresh	55 - 75
	Modeline "1280x1024_60.00"  109.00  1280  1368  1496  1712  1024  1027  1034  1063  -hsync  +vsync
EndSection

Section	"Device"
	Identifier	"Device0"
	Driver		"nv"
	VendorName	"geforce 6600"
EndSection

Section	"Screen"
	Identifier	"Screen0"
	Device		"Device0"
	Monitor		"Monitor0"
	DefaultDepth	16
	SubSection	"Display"
		Depth	24
		Modes	"1280x1024"
	EndSubSection
EndSections
```

[COLOR="Red"]EDIT[/COLOR]

Fixed by rebooting a couple of times by changing Driver to "nvidia" instead of nv

Thanks again jasonab1!

---

