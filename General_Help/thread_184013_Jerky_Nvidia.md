---
title: "Jerky Nvidia"
date: 2006-05-29
forum: General Help
---

### Post by dan_kent on 2006-05-29
Hello

I'm going mad trying to get my Nivdia card wortking smoothly. I've followed all the how to's a dn tips I can find and I've got in installed and worked, but it's very jerky. Glxgears works for example but the cogs keep sticking. I've included the relevent section of my xorg below. Does anyone have any suggestions?

Section "Module"
    Load           "dbe"
    Load           "extmod"
    Load           "type1"
    Load           "freetype"
    Load           "glx"
EndSection

Section "Device"
    Identifier     "Device0"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    Option         "NoLogo" "on"
    Option         "RenderAccel" "true"
    Option         "BackingStore" "On"
    Option         "NvAgp" "1"
    Option         "DPMS"
    Option         "Coolbits" "1"
EndSection

Section "Screen"
    Identifier     "Screen0"
    Device         "Device0"
    Monitor        "Monitor0"
    DefaultDepth    24
    SubSection     "Display"
        Depth       24
        Modes      "1024x768" "800x600" "640x480"
    EndSubSection
EndSection

Dan

---

### Post by treris on 2006-05-29
I'm not exactly sure, but my xorg.conf looks very different, 

[I]Section "Device"
	Identifier	"NVIDIA Corporation NV43 [GeForce 6600 GT]"
	Driver		"nvidia"
	BusID		"PCI:1:0:0"
EndSection

Section "Monitor"
	Identifier	"Generic Monitor"
	Option		"DPMS"
	HorizSync	28-184
	VertRefresh	43-160
	Modeline	"1280x800@60" 83.91 1280 1312 1624 1656 800 816 824 841
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"NVIDIA Corporation NV43 [GeForce 6600 GT]"
	Monitor		"Generic Monitor"
	DefaultDepth	24
	SubSection "Display"
		Depth		1
		Modes		"1680x1050" "1600x1200" "1440x900" "1400x1050" "1280x1024" "1280x960" "1280x854" "1280x800" "1280x768" "1200x800" "1152x864" "1152x768" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1680x1050" "1600x1200" "1440x900" "1400x1050" "1280x1024" "1280x960" "1280x854" "1280x800" "1280x768" "1200x800" "1152x864" "1152x768" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1680x1050" "1600x1200" "1440x900" "1400x1050" "1280x1024" "1280x960" "1280x854" "1280x800" "1280x768" "1200x800" "1152x864" "1152x768" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1680x1050" "1600x1200" "1440x900" "1400x1050" "1280x1024" "1280x960" "1280x854" "1280x800" "1280x768" "1200x800" "1152x864" "1152x768" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1680x1050" "1600x1200" "1440x900" "1400x1050" "1280x1024" "1280x960" "1280x854" "1280x800" "1280x768" "1200x800" "1152x864" "1152x768" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1680x1050" "1600x1200" "1440x900" "1400x1050" "1280x1024" "1280x960" "1280x854" "1280x800" "1280x768" "1200x800" "1152x864" "1152x768" "1024x768" "800x600" "640x480"
	EndSubSection
EndSection[/I]

could you be a little more specific in what you have done so far and also what kind of nvidia card you're trying to get working properly?

PS I should really clean up my xorg.conf and get rid of a lot of lines with options I'll never use;)

---

### Post by dan_kent on 2006-05-29
The card I believe is an Nvidia FX5600

I've followed all three sets of instructions at

[http://doc.gwos.org/index.php/Latest_Nvidia_Dapper](http://doc.gwos.org/index.php/Latest_Nvidia_Dapper)

I've also tried using the script found in these forums. 

What's even more maddening though is that I did have everyrthing working fine at one point. It stopped work after an update - which I assume must be one of the Xorg  ones.

---

### Post by tseliot on 2006-05-29
[QUOTE=dan_kent]What's even more maddening though is that I did have everyrthing working fine at one point. It stopped work after an update - which I assume must be one of the Xorg  ones.[/QUOTE]
If that's the problem just reinstall the driver

---

### Post by dan_kent on 2006-05-29
I've done that. I've installed and reinstalled both the 8756 and drivers 8762, and back again.

---

### Post by tseliot on 2006-05-29
[QUOTE=dan_kent]I've done that. I've installed and reinstalled both the 8756 and drivers 8762, and back again.[/QUOTE]
Option "RenderAccel" "true" is enabled by default by those driver. Please remove it from your xorg.conf.

Another thing: is glxgears the only problem you have with the driver?

---

### Post by dan_kent on 2006-05-29
I have now removed RenderAccel - it's still jerking though.

Glxgears isn't the only thing that's show the jerking - it's anthing that uses GL - Neverwinter Night and Enemy Territory for example.

---

