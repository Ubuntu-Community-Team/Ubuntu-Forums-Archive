---
title: "Trying to change resolutions"
date: 2006-06-12
forum: General Help
---

### Post by CujoQuarrel on 2006-06-12
New installation on a Dell 6000 laptop. 

I'm trying to change the resolution to a lower resolution from the default 
1600x1200 (going for 1280x960). 

Tried running the pkg-reconfigure xserver-xorg and no joy.

Hand edited the xorg.conf file to be the following removing all references to 1600x1200.


Section "Device"
	Identifier	"Intel Corporation Mobile 915GM/GMS/910GML Express Graphics Controller"
	Driver		"i810"
	BusID		"PCI:0:2:0"
EndSection

Section "Monitor"
	Identifier	"Generic Monitor"
	Option		"DPMS"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"Intel Corporation Mobile 915GM/GMS/910GML Express Graphics Controller"
	Monitor		"Generic Monitor"
	DefaultDepth	24
	SubSection "Display"
		Depth		1
		Modes		"1280x960"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1280x960"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1280x960"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1280x960"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1280x960"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1280x960"
	EndSubSection
EndSection


And still I get a 1600x1200 screen. 

Where is it getting the resolution info from?

Thanks

---

### Post by mlind on 2006-06-12
Did you restart X server?

/var/log/Xorg.0.log contains information about what display modes are considered
when creating the X server instance.

---

### Post by CujoQuarrel on 2006-06-12
I rebooted the X server several times .

In that log file it appears that is it querying the hardware and getting the max resolution back. I see lines saying things like

(II) I810(0): Display Info: LFP (local flat panel): attached: TRUE, present: TRUE, size: (1920,1200)
(II) I810(0): Size of device LFP (local flat panel) is 1920 x 1200
(II) I810(0): Lowest common panel size for pipe B is 1920 x 1200
(II) I810(0): PanelID returned panel resolution : 1920x1200
(II) I810(0): h_active: 1920  h_sync: 2020  h_sync_end 2108 h_blank_end 2160 h_border: 0
(II) I810(0): h_active: 1920  h_sync: 2020  h_sync_end 2108 h_blank_end 2160 h_border: 0


Any way to override this? On this monitor this resolution makes it difficult to read things.

---

