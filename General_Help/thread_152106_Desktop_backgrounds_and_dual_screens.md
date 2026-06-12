---
title: "Desktop backgrounds and dual screens"
date: 2006-03-29
forum: General Help
---

### Post by gmclachl on 2006-03-29
I have set up dual monitors for my desktop, everything works great apart from one annoying little problem. The background is stretched across both screens, is it possible to have different wallpapers on each monitor.

Thanks.
 George

---

### Post by varunus on 2006-03-29
There is a quick little hack you could do; You could just open up the GIMP, and merge the two wallpapers into one wallpaper file so it would stretch out across properly...

There's probably a better way to do this though...

---

### Post by gmclachl on 2006-03-29
Hmmm, it seems as if it is treating the monitors as one big screen, when in fact I want 2 seperate screens, although  I don't want them to be clones of each other. 

 Is there a way to have 2 distinct screens but still have the ability to drag windows between each. 

 Here is the section for my xorg.conf 

Section "Device"
	Identifier	"NVIDIA Corporation NVIDIA Default Card"
	Driver		"nvidia"
	BusID		"PCI:1:0:0"
 	Option          "TwinView" "on"
       Option          "MetaModes" "1280x1024,1280x1024"
       Option          "SecondMonitorHorizSync" "28-80"
       Option          "SecondMonitorVertRefresh" "43-60"
       Option          "TwinViewOrientation" "LeftOf"   
EndSection

Section "Monitor"
	Identifier	"Generic Monitor"
	Option		"DPMS"
	HorizSync	28-64
	VertRefresh	43-60
EndSection


Section "Screen"
	Identifier	"Default Screen"
	Device		"NVIDIA Corporation NVIDIA Default Card"
	Monitor		"Generic Monitor"
	DefaultDepth	24
	SubSection "Display"
		Depth		1
		Modes		"1280x1024" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1280x1024" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1280x1024" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1280x1024" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1280x1024" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1280x1024" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
EndSection

George

---

