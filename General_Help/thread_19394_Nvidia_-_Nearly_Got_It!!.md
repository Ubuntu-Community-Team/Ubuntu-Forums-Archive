---
title: "Nvidia - Nearly Got It!!"
date: 2005-03-11
forum: General Help
---

### Post by saBrEwolf on 2005-03-11
Hi, I'm having a problem with the Nvidia 6629 drivers on Warty.

I downloaded the driver from nvidia and then installed as normal (letting it create its own kernel interface). I then set about trying to enable the driver, but every time I try, when X starts I just get a blank screen or the screen switches to stndby.

Most recently, I added a couple of settings to XF86Config-4 (I found the extra settings on cedega forum) and I now end up with the Nvidia logo appearing and then being pushed onto tty1

This is my XF86Config

Section "Files"
	FontPath	"unix/:7100"			# local font server
	# if the local font server has problems, we can fall back on these
	FontPath	"/usr/lib/X11/fonts/misc"
	FontPath	"/usr/lib/X11/fonts/cyrillic"
	FontPath	"/usr/lib/X11/fonts/100dpi/:unscaled"
	FontPath	"/usr/lib/X11/fonts/75dpi/:unscaled"
	FontPath	"/usr/lib/X11/fonts/Type1"
	FontPath	"/usr/lib/X11/fonts/CID"
	FontPath	"/usr/lib/X11/fonts/Speedo"
	FontPath	"/usr/lib/X11/fonts/100dpi"
	FontPath	"/usr/lib/X11/fonts/75dpi"
        # paths to defoma fonts
	FontPath	"/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
	FontPath	"/var/lib/defoma/x-ttcidfont-conf.d/dirs/CID"
EndSection

Section "Module"
#Load	"GLcore"
	Load	"bitmap"
	Load	"dbe"
	Load	"ddc"
#Load	"dri"
	Load	"extmod"
	Load	"freetype"
	Load	"glx"
	Load	"int10"
	Load	"record"
	Load	"speedo"
	Load	"type1"
	Load	"v4l"
	Load	"vbe"
	Load	"xtt"
EndSection

Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"keyboard"
	Option		"CoreKeyboard"
	Option		"XkbRules"	"xfree86"
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"gb"
EndSection

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
	Option		"Device"		"/dev/input/mice"
	Option		"Protocol"		"ImPS/2"
	Option		"Emulate3Buttons"	"true"
	Option		"ZAxisMapping"		"4 5"
EndSection

Section "Device"
	Identifier	"NVIDIA Corporation NV18 [GeForce4 MX 4000 AGP 8x]"
	Driver		"nvidia"
	Option 		"NvAGP" 		"1"
	Option 		"DPMS" 
	BusID		"PCI:1:0:0"
EndSection

Section "Monitor"
	Identifier	"DELL D828L"
	HorizSync	30-54
	VertRefresh	48-120
	Option		"DPMS"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"NVIDIA Corporation NV18 [GeForce4 MX 4000 AGP 8x]"
	Monitor		"DELL D828L"
	DefaultDepth	24
	SubSection "Display"
		Depth		1
		Modes		"1024x768" "800x600" "720x400" "720x350" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1024x768" "800x600" "720x400" "720x350" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1024x768" "800x600" "720x400" "720x350" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1024x768" "800x600" "720x400" "720x350" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1024x768" "800x600" "720x400" "720x350" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1024x768" "800x600" "720x400" "720x350" "640x480"
	EndSubSection
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		"Default Screen"
	InputDevice	"Generic Keyboard"
	InputDevice	"Configured Mouse"
EndSection

Section "DRI"
	Mode	0666
EndSection

Any help would be very much appreciated

Note: Before downloading the Nvidia drivers from nvidia, I tried the ones in universe.. I have left these on, could there be conflict here?

---

### Post by carney1979 on 2005-03-11
There is a new driver. The 6629 driver was VERY buggy.

Go get the new (released today, March 11, 2005) driver from nvidia's site.

Be sure you remove nvidia-glx before installing the Nvidia driver.

sudo apt-get remove --purge nvidia-glx

Best of luck!

David

---

### Post by saBrEwolf on 2005-03-12
[QUOTE=carney1979]There is a new driver. The 6629 driver was VERY buggy.

Go get the new (released today, March 11, 2005) driver from nvidia's site.

Be sure you remove nvidia-glx before installing the Nvidia driver.

sudo apt-get remove --purge nvidia-glx

Best of luck!

David[/QUOTE]
 Wahey! It works,
Thanks very much David :D

---

### Post by poyner on 2005-03-14
[QUOTE=carney1979]There is a new driver. The 6629 driver was VERY buggy.

Go get the new (released today, March 11, 2005) driver from nvidia's site.

Be sure you remove nvidia-glx before installing the Nvidia driver.

sudo apt-get remove --purge nvidia-glx

Best of luck!

David[/QUOTE]

hmmm ok... i've got an nVidia FX5200... after installing the nvidia drivers I felt that things were slower using them than the nv drivers.... so I changed back. maybe the new drivers would be better? 

anyway, I downloaded the new ones from nvidia but when i try and install them it says something about needing the kernel source files? can someone let me know where I get these from? thanks heaps.

edit: ignore my last.... i managed to sort it all out.... It does feel a fair bit quicker although i'm not sure if it's the new drivers or because I also disabled dri.... either way... i'm happy.

---

