---
title: "looking for an xorg.conf explanation"
date: 2011-04-26
forum: General Help
---

### Post by modsbyus on 2011-04-26
Below is my xorg.conf. I have tried searching for an explanation of the things I see in the file and haven't really found anything. 
For Example: what does this mean?  
[COLOR="DarkOrange"]Section "ServerLayout"
	Identifier     "aticonfig Layout"
	Screen      0  "aticonfig-Screen[0]-0" 0 0

[/COLOR]
I am having some issues with overscan. I have a rear projection tv as my monitor. In the ati (admin) ccc I dont have a slider as mentioned in many other forum posts. Also I have already run ```
sudo aticonfig --tv-geometry=85x90+10-10
```
and as you can see in my config file the changes were made there but I am still having overscanning issues. (I can't see the top and bottom portions of my screen.) This is also the case when hooked up to my plasma tv so I know its not the tv.
Neither one of the tvs have an overscan control in the menu.
I am hoping to get an explanation of the terms used through out my xorg.conf file in order to try to find a work around.
Thank you for any assistance.

Section "ServerLayout"
	Identifier     "aticonfig Layout"
	Screen      0  "aticonfig-Screen[0]-0" 0 0
EndSection

Section "Module"
EndSection

Section "Monitor"
	Identifier   "aticonfig-Monitor[0]-0"
	Option	    "VendorName" "ATI Proprietary Driver"
	Option	    "ModelName" "Generic Autodetecting Monitor"
	Option	    "DPMS" "true"
EndSection

Section "Device"
	Identifier  "ATI Technologies Inc RV620 LE [Radeon HD 3450] (prog-if 00 [VGA controller])"
	Driver      "fglrx"
	Option	    "TVVPosAdj" "-10"
	Option	    "TVHPosAdj" "+10"
	Option	    "TVVSizeAdj" "90"
	Option	    "TVHSizeAdj" "85"
	BusID       "PCI:1:0:0"
EndSection

Section "Screen"
	Identifier "aticonfig-Screen[0]-0"
	Device     "aticonfig-Device[0]-0"
	Monitor    "aticonfig-Monitor[0]-0"
	DefaultDepth     24
	SubSection "Display"
		Viewport   0 0
		Depth     24
	EndSubSection
EndSection

---

### Post by lithopsian on 2011-04-26
The layout section just points the config to the correct screen section.  The screen section then points to the correct monitor and device sections.  The screen, device, monitor, and module sections all actually configure stuff!  In your case, the module section does nothing.

I don't know how to fix your problem.  The device and screen section options are often specific to the card you are using and I don't know where the correct documentation for your card is, or even if it exists.

---

### Post by modsbyus on 2011-04-26
> **lithopsian said:**
> The layout section just points the config to the correct screen section.  The screen section then points to the correct monitor and device sections.  The screen, device, monitor, and module sections all actually configure stuff!  In your case, the module section does nothing.

I don't know how to fix your problem.  The device and screen section options are often specific to the card you are using and I don't know where the correct documentation for your card is, or even if it exists.

Thank you for your response. However, I was looking for something a little more specific. 
Like... what kind of functional modifications can I do with this (Monitor "aticonfig-Monitor[0]-0") What is the [0]-0") for... etc..

---

### Post by modsbyus on 2011-04-26
I have also tried going into the driver config filesand disabling tvoverscanenable by switching it from v1 to v0. I dont know if that helps or not but it didnt work.

---

