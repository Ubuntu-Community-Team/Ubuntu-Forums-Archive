---
title: "Vsync ?"
date: 2006-04-07
forum: General Help
---

### Post by Tamale on 2006-04-07
Hi.. it appears I don't have vsync enabled on my toshiba laptop with an nvidia geforce 5200 go.. the screensavers all tear really badly.. anyway I can fix this?  I did get the new nvidia drivers successfully installed though.

---

### Post by trent dillman on 2006-04-07
Post the monitor section of your org.conf...

---

### Post by Tamale on 2006-04-08
```
Section "Device"
	Identifier	"NVIDIA Corporation NV34M [GeForce FX Go 5200]"
	Driver		"nvidia"
	BusID		"PCI:1:0:0"
EndSection

Section "Monitor"
	Identifier	"Generic Monitor"
	Option		"DPMS"
	HorizSync	28-64
	VertRefresh	43-60
	Modeline	"1280x800@60" 83.91 1280 1312 1624 1656 800 816 824 841
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"NVIDIA Corporation NV34M [GeForce FX Go 5200]"
	Monitor		"Generic Monitor"
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
```

---

