---
title: "Can't Get 1280x1024 Screen Resolution Ubuntu 11.04"
date: 2011-06-29
forum: General Help
---

### Post by Addiaz on 2011-06-29
Hello Guys

I'm here to ask for your help in a trouble. I can't get 1280*1024 screen reolution!

I am using Ubuntu 11.04 on a Desktop. My graphic card is ATI Radeon HD 4350, the processor is an Intel Pentium 4. 2 GB RAM.

I installed ubuntu and things were ok, not the screen resolution that I wanted but things were fine. Then I followed a tutorial to create xorg.conf file in Ubuntu 11, I did it,it worked fine. Then I installed the privative drivers for my GPU.

The drivers are called: Controlador Gráfico FGLRX privativo para ATI/AMD (I use ubuntu in spanish, my native language)

As i said, I activated/installed them, then I rebooted the pc, and my monitor showed up a message: "Modo No Soportado" (Mode not supported)  But I could continue working fine, then an Ubuntu message showed up too saying that my GPU or something like that wasn't able to run Unity (I was able to run it before installing those drivers) 


Well the I tried to change my screen resolution but I did not find 1280x1024. SO i tried to edit the recently created xorg.conf file. I didn't figure out how to set up my resolution, Once I followed a tutorial to do it and It said I had to change some screen values... but I didn't find them.

So guys, I paste her emy xorg.conf file:

> 
Section "Files"
	ModulePath   "/usr/lib/xorg/modules"
	FontPath     "/usr/share/fonts/X11/misc"
	FontPath     "/usr/share/fonts/X11/cyrillic"
	FontPath     "/usr/share/fonts/X11/100dpi/:unscaled"
	FontPath     "/usr/share/fonts/X11/75dpi/:unscaled"
	FontPath     "/usr/share/fonts/X11/Type1"
	FontPath     "/usr/share/fonts/X11/100dpi"
	FontPath     "/usr/share/fonts/X11/75dpi"
	FontPath     "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
	FontPath     "built-ins"
EndSection

Section "Monitor"
	Identifier   "Monitor0"
	VendorName   "Monitor Vendor"
	ModelName    "Monitor Model"
EndSection

Section "Monitor"
	Identifier   "Monitor1"
	VendorName   "Monitor Vendor"
	ModelName    "Monitor Model"
EndSection

Section "Monitor"
	Identifier   "Monitor2"
	VendorName   "Monitor Vendor"
	ModelName    "Monitor Model"
EndSection

Section "Screen"
	Identifier "Screen0"
	Device     "Card0"
	Monitor    "Monitor0"
	DefaultDepth	24
	SubSection "Display"
		Viewport   0 0
		Depth     1
	EndSubSection
	SubSection "Display"
		Viewport   0 0
		Depth     4
	EndSubSection
	SubSection "Display"
		Viewport   0 0
		Depth     8
	EndSubSection
	SubSection "Display"
		Viewport   0 0
		Depth     15
	EndSubSection
	SubSection "Display"
		Viewport   0 0
		Depth     16
	EndSubSection
	SubSection "Display"
		Viewport   0 0
		Depth     24
	EndSubSection
EndSection

Section "Screen"
	Identifier "Screen1"
	Device     "Card1"
	Monitor    "Monitor1"
	SubSection "Display"
		Viewport   0 0
		Depth     1
	EndSubSection
	SubSection "Display"
		Viewport   0 0
		Depth     4
	EndSubSection
	SubSection "Display"
		Viewport   0 0
		Depth     8
	EndSubSection
	SubSection "Display"
		Viewport   0 0
		Depth     15
	EndSubSection
	SubSection "Display"
		Viewport   0 0
		Depth     16
	EndSubSection
	SubSection "Display"
		Viewport   0 0
		Depth     24
	EndSubSection
EndSection

Section "Screen"
	Identifier "Screen2"
	Device     "Card2"
	Monitor    "Monitor2"
	SubSection "Display"
		Viewport   0 0
		Depth     1
	EndSubSection
	SubSection "Display"
		Viewport   0 0
		Depth     4
	EndSubSection
	SubSection "Display"
		Viewport   0 0
		Depth     8
	EndSubSection
	SubSection "Display"
		Viewport   0 0
		Depth     15
	EndSubSection
	SubSection "Display"
		Viewport   0 0
		Depth     16
	EndSubSection
	SubSection "Display"
		Viewport   0 0
		Depth     24
	EndSubSection
EndSection

Section "Module"
	Load  "glx"
	Load  "extmod"
	Load  "record"
	Load  "dri"
	Load  "dbe"
	Load  "dri2"
EndSection

Section "InputDevice"
	Identifier  "Keyboard0"
	Driver      "kbd"
EndSection

Section "InputDevice"
	Identifier  "Mouse0"
	Driver      "mouse"
	Option	    "Protocol" "auto"
	Option	    "Device" "/dev/input/mice"
	Option	    "ZAxisMapping" "4 5 6 7"
EndSection

Section "ServerLayout"
	Identifier     "X.org Configured"
	Screen      0  "Screen0" 0 0
	Screen      1  "Screen1" RightOf "Screen0"
	Screen      2  "Screen2" RightOf "Screen1"
	InputDevice    "Mouse0" "CorePointer"
	InputDevice    "Keyboard0" "CoreKeyboard"
EndSection

Section "Device"
	Identifier  "Card0"
	Driver      "radeon"
	BusID       "PCI:1:0:0"
EndSection

Section "Device"
	Identifier  "Card1"
	Driver      "fbdev"
	BusID       "PCI:1:0:0"
EndSection

Section "Device"
	Identifier  "Card2"
	Driver      "vesa"
	BusID       "PCI:1:0:0"
	### Available Driver options are:-
	### Values: <i>: integer, <f>: float, <bool>: "True"/"False",
	### <string>: "String", <freq>: "<f> Hz/kHz/MHz",
	### <percent>: "<f>%"
	### [arg]: arg optional
	#Option     "ShadowFB"           	# [<bool>]
	#Option     "DefaultRefresh"     	# [<bool>]
	#Option     "ModeSetClearScreen" 	# [<bool>]
EndSection
 

Please, i don't know what to do to fix this, I want my screen resolution and Unity interface back.

Thanks ;)

---

### Post by pqwoerituytrueiwoq on 2011-06-29
probably a driver issue see if you can find one for it

---

### Post by Addiaz on 2011-07-01
Thanks for your reply pqwoerituytrueiwoq
I tried downloading the 32bits Drivers from ATI webpage, but they just satrted to install and then stopped. Then I tried with 64bits drivers, maybe It could work... and I had the same result, stopped the installation.

But now that I think, maybe I should uninstall the first driver, the one that Ubuntu suggested me to Install. 

I'm gonna try that.
Thanks for your help. :D

---

### Post by Addiaz on 2011-07-02
> **pqwoerituytrueiwoq said:**
> probably a driver issue see if you can find one for it

Ok,I just uninstalled the driver suggested by ubuntu. The FUNNY thing is that Unity interface came back. 

Cool, with graphic drivers NO Unity "'cause your pc can't run it."
   Without graphic drivers, Unity runs perfectly.. :confused:

I'm gonna install the drivers I downloaded from ATI webpage, and I'll tell you what happened.

---

### Post by Addiaz on 2011-07-02
> **Addiaz said:**
> Ok,I just uninstalled the driver suggested by ubuntu. The FUNNY thing is that Unity interface came back. 

Cool, with graphic drivers NO Unity "'cause your pc can't run it."
   Without graphic drivers, Unity runs perfectly.. :confused:

I'm gonna install the drivers I downloaded from ATI webpage, and I'll tell you what happened.

I had no luck. I got some errors related to xorg.conf So I deleted it. Still have Unity. I attempt to install the drivers, but I couldn't, same error related to xorg..

I'm going back to Linux Mint 10 or 11 

Thanks for the help.

---

