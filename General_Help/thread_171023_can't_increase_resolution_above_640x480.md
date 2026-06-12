---
title: "can't increase resolution above 640x480"
date: 2006-05-05
forum: General Help
---

### Post by d3dtn01 on 2006-05-05
I've got a Dell B120 laptop. I'm trying to get Ubuntu to work with my external monitor (a NEC MultiSync XV17). Right now, I can only view in 640x480 resolution. I went through forums and other Web sites (including this HowTo: [HowTo: change resolution/refresh rate in Xorg]("http://www.ubuntuforums.org/showthread.php?t=83973")) and followed many directions but still I can't select anything but 640x480. Here's the relevant portion of my xorg.conf file:

Section "Device"
	Identifier	"Intel Corporation Intel Default Card"
	Driver		"i810"
	BusID		"PCI:0:2:0"
EndSection

Section "Monitor"
	Identifier	"Monitor0"
	Option		"DPMS"
	Modeline	"1280x800@60" 83.91 1280 1312 1624 1656 800 816 824 841 +hsync +vsync
EndSection

Section "Monitor"
	Identifier	"Monitor1"
	VendorName	"NEC"
	ModelName	"MultiSync XV17"
	HorizSync	31 - 65
	VertRefresh	55 - 100
	Option		"DPMS"
	Modeline	"1024x768" 60.80 1024 1056 1128 1272 768 768 770 796 -HSync +Vsync
EndSection
	

Section "Screen"
	Identifier	"Screen0"
	Device		"Intel Corporation Intel Default Card"
	Monitor		"Monitor0"
	DefaultDepth	24
	SubSection "Display"
		Depth		1
		Modes		"1280x800"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1280x800"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1280x800"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1280x800"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1280x800"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1280x800"
	EndSubSection
EndSection

Section "Screen"
	Identifier	"Screen1"
	Device		"Intel Corporation Intel Default Card"
	Monitor		"Monitor1"
	DefaultDepth	24
	SubSection "Display"
		Depth		1
		Modes		"1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1024x768" "800x600" "640x480"
	EndSubSection
EndSection


Section "ServerLayout"
	Identifier	"Layout0"
	Screen		"Screen0"
	InputDevice	"Generic Keyboard"
	InputDevice	"Configured Mouse"
	InputDevice	"Synaptics Touchpad"
EndSection

Section "ServerLayout"
	Identifier	"Layout1"
	Screen		"Screen1"
	InputDevice	"Generic Keyboard"
	InputDevice	"Configured Mouse"
	InputDevice	"Synaptics Touchpad"
EndSection

Section "ServerLayout"
	Identifier	"Dual-Monitor"
	Screen 0	"Screen0" LeftOf "Screen1"
	Screen 1	"Screen1" 0 0
	InputDevice	"Generic Keyboard"
	InputDevice	"Configured Mouse"
	InputDevice	"Synaptics Touchpad"
EndSection

What am I doing wrong?

---

### Post by nismoskys on 2006-05-05
so you've tried running
```
sudo dpkg-reconfigure xserver-xorg
```
already?

---

### Post by nismoskys on 2006-05-05
okay if you havent already tried running the above listed command, try this..

replace the **Section "Device"** in your xorg.conf to
```
Section "Device"
	Identifier "Intel Corporation Intel Default Card"
	Driver "i810"
	BusID "PCI:0:2:0"
	Option "MetaModes" "1024x768,1024x768;800x600,800x600;640x480,640x480;"
EndSection
```

i think it should work because thats where the resolutions are listed in my xorg.conf, but i have an nvidia geforce card, so im not sure if the same will work for you.

Dont forget to restart X after you save the changes to your xorg.conf.

---

### Post by d3dtn01 on 2006-05-08
Yes, I already ran:

```
sudo dpkg-reconfigure xserver-xorg
```

I also modified my xorg.conf file based on your suggestion below:

```
Section "Device"
	Identifier "Intel Corporation Intel Default Card"
	Driver "i810"
	BusID "PCI:0:2:0"
	Option "MetaModes" "1024x768,1024x768;800x600,800x600;640x480,640x480;"
EndSection
```

This didn't work either. Thanks for the advice, though. Any other ideas?

---

### Post by nismoskys on 2006-05-08
i dont know man, the only thing i can think of now is that if you havent already, restart your computer fully, cuz that's solved alot of problems for me in the past.

---

### Post by d3dtn01 on 2006-05-09
I repeated dpkg-reconfigure. So now when I boot with the external monitor I get the right resolution. I went to look at my backup xorg.conf and can't see any differences.  I'm not sure what I did different this time. It mystifies me. Thanks for the advice.

---

### Post by nismoskys on 2006-05-10
no problem, glad you got it working.

---

### Post by CameronCalver on 2006-05-12
when do what it says in the how to my screen goes blakc and it says login how do i get out of that view and back to normal mode

---

### Post by nismoskys on 2006-05-12
after you login type ```
startx
```

---

