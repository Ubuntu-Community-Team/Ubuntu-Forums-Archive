---
title: "Nvidia 7600 Composite no available"
date: 2010-03-12
forum: General Help
---

### Post by ear9mrn on 2010-03-12
I am running kernel 2.6.31-20-generic Karmic with a Nvidia GeForce 7600 GS video card. I have the Nvidia 185.18.36 (recommended) hardware driver. Before the most recent kernel upgrade (31-17 to 31-20) compiz was working fine (wobbly windows and everything). Now whenever I try and select "extra" under visual effects I get an error saying "The Composite extension is not available".

Any suggestions ?

I include my xorg.conf if that helps.

Thanks,

Pete.

```

Section "Monitor"
	Identifier     "Configured Monitor"
EndSection

Section "Monitor"
	Identifier     "Monitor0"
	VendorName     "Unknown"
	ModelName      "Samsung SyncMaster"
	HorizSync       30.0 - 75.0
	VertRefresh     56.0 - 61.0
EndSection

Section "Monitor"
	Identifier     "Monitor1"
	VendorName     "Unknown"
	ModelName      "OPTi OptomaHD70 v2"
	HorizSync       15.0 - 120.0
	VertRefresh     15.0 - 99.0
	#    HorizSync      15.0 - 75.0
	#    VertRefresh    60.0 - 85.0
EndSection

Section "Screen"
	Identifier     "Default Screen"
	Device         "Configured Video Device"
	Monitor        "Configured Monitor"
	DefaultDepth	24
EndSection

Section "Screen"
	Identifier     "Screen0"
	Device         "Device0"
	Monitor        "Monitor0"
	DefaultDepth    24
	Option         "TwinView" "0"
	Option         "TwinViewXineramaInfoOrder" "CRT-0"
	Option         "metamodes" "CRT: nvidia-auto-select +0+0"
	SubSection "Display"
		Depth       24
	EndSubSection
EndSection

Section "Screen"
	Identifier     "Screen1"
	Device         "Device1"
	Monitor        "Monitor1"
	DefaultDepth    24
	Option         "TwinView" "0"
	Option         "metamodes" "DFP: 1920x1080 +0+0"
	# Removed Option "metamodes" "DFP: nvidia-auto-select +0+0"
	SubSection "Display"
		Depth       24
	EndSubSection
EndSection

Section "Module"
	Load           "glx"
EndSection


Section "Extensions"
	Option         	"Composite" "Enable"
	#Option         "Composite" "Disable"
EndSection

Section "ServerLayout"
	Identifier     "Default Layout"
	Screen      	0  "Screen0" 0 0
	Screen      	1  "Screen1" RightOf "Screen0"
	InputDevice    "Keyboard0" "CoreKeyboard"
	InputDevice    "Mouse0" "CorePointer"
EndSection

Section "Device"
	Identifier     "Configured Video Device"
	Driver         "nvidia"
	Option         "NoLogo" "True"
	Option         "UseEvents" "True"
EndSection

Section "Device"
	Identifier     	"Device0"
	VendorName     	"NVIDIA Corporation"
	BoardName      	"GeForce 7600 GS"
	Option 		"RenderAccel" "on"
	Option 		"UseEvents" "on"
	Option        	"AllowGLXWithComposite" "true"
	BusID          	"PCI:1:0:0"
	Screen          0
	Driver		"nvidia"
	Option		"NoLogo"	"True"
EndSection

Section "Device"
	Identifier     	"Device1"
	VendorName     	"NVIDIA Corporation"
	Option          "RenderAccel" "on"
        Option          "UseEvents" "on"
        Option          "AllowGLXWithComposite" "true"
	BoardName      	"GeForce 7600 GS"
	BusID          	"PCI:1:0:0"
	Screen          1
	Driver		"nvidia"
	Option		"NoLogo"	"True"
EndSection

Section "ServerFlags"
	Option         "Xinerama" "1"
EndSection

```

---

