---
title: "Stuttering pixelated avi's"
date: 2009-06-30
forum: General Help
---

### Post by Voorhees1979 on 2009-06-30
Hi all

I have a slight problem with movie playback. Its basically a fresh install of Hardy with all the updates. PC is 2.6ghz P4, 1G of Ram and an ATI X800 XT 256m Graphics Card. So the system is powerful enough. I have a feeling the issue is a graphics driver. After the fresh install I went to System>Admin>Hardware Drivers. This installed the ATI accelerated graphics driver with a tick beside in use. Im guessing this is wrong. Should I install the ATI driver from the ATI website? Im only guessing its a graphics driver problem. If anyone could help get the card working 100% I would be very pleased

Xorg

Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"gb"
EndSection

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
EndSection

Section "Device"
	Identifier	"Configured Video Device"
	Driver		"fglrx"
EndSection

Section "Monitor"
	Identifier	"Configured Monitor"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
	Defaultdepth	24
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
  screen "Default Screen"
EndSection
Section "Module"
	Load		"glx"
EndSection

---

### Post by Voorhees1979 on 2009-07-02
Doesnt matter. Actually moved over to Mepis. 100 times faster, soon as an app is clicked its already loaded and ready to use, not as bloated and detected everything and it worked out the box. Thanks Ubuntu for the years learning curve. Time to move on to better things :)

---

