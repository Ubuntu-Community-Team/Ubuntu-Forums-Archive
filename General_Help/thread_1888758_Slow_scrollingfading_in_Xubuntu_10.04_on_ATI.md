---
title: "Slow scrolling\fading in Xubuntu 10.04 on ATI"
date: 2011-11-30
forum: General Help
---

### Post by NekoMaster on 2011-11-30
Alright, back to my usual tinkering around in Xubuntu, this time falling back to 10.04 LTS for its ability to run programs from flash drives and other external media :)

Though one thing that surprised me is that right off the hop I was having problems with my video card when I first installed Xubuntu 10.04 (32 bit)

Im running on a Sapphire Radeon HD 6570 1GB GDDR3 Video card, and my first problem (which was solved by installing the drivers) was not being able to set the desktop resolution to my 17" wide screen LCD's native resolution.

~ ! ~ IMPORTANT PART ~ ! ~

My new problem came after I installed the drivers (which I had to do manually) for my Radeon HD 6570. Now in all my windows scrolling is really slow, even getting choppy in Firefox or when I'm scrolling in the setting's windows. The fade in and out that happens when asking for admin privileges and password is also fairly slow and choppy.

Heres my xorg configuration file.

```
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
	Identifier  "aticonfig-Device[0]-0"
	Driver      "fglrx"
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


```

Hopefully someone can help me with this so I can stay on Xubuntu for my General stuff like browsing and videos? As much as I like Windows 7 my love for Linux keeps me coming back ^_^

Timely help would be nice (though I dont expect help at 2am EST)

---

