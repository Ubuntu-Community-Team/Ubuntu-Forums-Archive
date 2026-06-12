---
title: "Resolution stock on 800x600 :( Please Help!"
date: 2005-03-05
forum: General Help
---

### Post by KpNemo on 2005-03-05
Hi, sorry for my English, I am russian. 
My problem is:
Then i working on "nv" drivers, evrything fine, I get my 1024x768
I installed nvidia drivers, and enable it, and now i stock with 800x600 resolution.
Here is settings drom XFree86:

Section "Device"
	Identifier	"NVIDIA Corporation NV17 [GeForce4 420 Go]"
	Driver		"nvidia"
	BusID		"PCI:1:0:0"
EndSection

Section "Monitor"
	Identifier	"Generic Monitor"
	HorizSync	28-49
	VertRefresh	43-72
	Option		"DPMS"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"NVIDIA Corporation NV17 [GeForce4 420 Go]"
	Monitor		"Generic Monitor"
	DefaultDepth	24
	SubSection "Display"
		Depth		1
		Modes		"1152x864" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1152x864" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1152x864" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1152x864" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1152x864" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1152x864" "1024x768" "800x600" "640x480"
	EndSubSection
EndSection

I also try to make something with sudo dpkg-reconfigure xserver-xfree86
but no luck :(
I read in this forum many threads about it, but no found solution. 
If anybody know how to rule this problem, a will be a great thankfull.
10x anyway.

---

### Post by KpNemo on 2005-03-06
[QUOTE=KpNemo]Hi, sorry for my English, I am russian. 
My problem is:
Then i working on "nv" drivers, evrything fine, I get my 1024x768
I installed nvidia drivers, and enable it, and now i stock with 800x600 resolution.
Here is settings drom XFree86:

Section "Device"
	Identifier	"NVIDIA Corporation NV17 [GeForce4 420 Go]"
	Driver		"nvidia"
	BusID		"PCI:1:0:0"
EndSection

Section "Monitor"
	Identifier	"Generic Monitor"
	HorizSync	28-49
	VertRefresh	43-72
	Option		"DPMS"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"NVIDIA Corporation NV17 [GeForce4 420 Go]"
	Monitor		"Generic Monitor"
	DefaultDepth	24
	SubSection "Display"
		Depth		1
		Modes		"1152x864" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1152x864" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1152x864" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1152x864" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1152x864" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1152x864" "1024x768" "800x600" "640x480"
	EndSubSection
EndSection

I also try to make something with sudo dpkg-reconfigure xserver-xfree86
but no luck :(
I read in this forum many threads about it, but no found solution. 
If anybody know how to rule this problem, a will be a great thankfull.
10x anyway.[/QUOTE]
 hi one more time
i found solution to this thing 
just add:

Section "Device"
	Identifier	"NVIDIA Corporation NV17 [GeForce4 420 Go]"
	Driver		"nvidia"
	BusID		"PCI:1:0:0"
        Option        "RenderAccel"        "true"
        Option        "NvAGP"            "3"
        Option         "IgnoreEDID"          "true"
EndSection

3 options like i did, and comment GLcore and DRI 
thats all, working fine in my case :) 
I home i helped to someone.

---

