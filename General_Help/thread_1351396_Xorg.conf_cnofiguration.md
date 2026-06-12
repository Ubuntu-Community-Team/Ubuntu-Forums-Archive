---
title: "Xorg.conf cnofiguration"
date: 2009-12-10
forum: General Help
---

### Post by domagoj91 on 2009-12-10
I need help with my Xorg.conf configuration.
I want beter 3D performance....
Can someone help me
Thanks..


```
Section "ServerLayout"
	Identifier     "X.org Configured"
	Screen      0  "Screen0" 0 0
	InputDevice    "Mouse0" "CorePointer"
	InputDevice    "Keyboard0" "CoreKeyboard"
EndSection

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

Section "Module"
	Load  "dri2"
	Load  "extmod"
	Load  "dri"
	Load  "record"
	Load  "dbe"
	Load  "glx"
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

Section "Monitor"
	#DisplaySize	  300   230	# mm
	Identifier   "Monitor0"
	VendorName   "AUO"
	ModelName    "f03"
EndSection

Section "Device"
        ### Available Driver options are:-
        ### Values: <i>: integer, <f>: float, <bool>: "True"/"False",
        ### <string>: "String", <freq>: "<f> Hz/kHz/MHz"
        ### [arg]: arg optional
        #Option     "NoAccel"            	# [<bool>]
        #Option     "SWcursor"           	# [<bool>]
        #Option     "Dac6Bit"            	# [<bool>]
        #Option     "Dac8Bit"            	# [<bool>]
        #Option     "BusType"            	# [<str>]
        #Option     "CPPIOMode"          	# [<bool>]
        #Option     "CPusecTimeout"      	# <i>
        #Option     "AGPMode"            	# <i>
        #Option     "AGPFastWrite"       	# [<bool>]
        #Option     "AGPSize"            	# <i>
        #Option     "GARTSize"           	# <i>
        #Option     "RingSize"           	# <i>
        #Option     "BufferSize"         	# <i>
        #Option     "EnableDepthMoves"   	# [<bool>]
        #Option     "EnablePageFlip"     	# [<bool>]
        #Option     "NoBackBuffer"       	# [<bool>]
        #Option     "DMAForXv"           	# [<bool>]
        #Option     "FBTexPercent"       	# <i>
        #Option     "DepthBits"          	# <i>
        #Option     "PCIAPERSize"        	# <i>
        #Option     "AccelDFS"           	# [<bool>]
        #Option     "IgnoreEDID"         	# [<bool>]
        #Option     "DisplayPriority"    	# [<str>]
        #Option     "PanelSize"          	# [<str>]
        #Option     "ForceMinDotClock"   	# <freq>
        #Option     "ColorTiling"        	# [<bool>]
        #Option     "VideoKey"           	# <i>
        #Option     "RageTheatreCrystal" 	# <i>
        #Option     "RageTheatreTunerPort" 	# <i>
        #Option     "RageTheatreCompositePort" 	# <i>
        #Option     "RageTheatreSVideoPort" 	# <i>
        #Option     "TunerType"          	# <i>
        #Option     "RageTheatreMicrocPath" 	# <str>
        #Option     "RageTheatreMicrocType" 	# <str>
        #Option     "ScalerWidth"        	# <i>
        #Option     "RenderAccel"        	# [<bool>]
        #Option     "SubPixelOrder"      	# [<str>]
        #Option     "ShowCache"          	# [<bool>]
        #Option     "ClockGating"        	# [<bool>]
        #Option     "VGAAccess"          	# [<bool>]
        #Option     "ReverseDDC"         	# [<bool>]
        #Option     "LVDSProbePLL"       	# [<bool>]
        #Option     "AccelMethod"        	# <str>
        #Option     "DRI"                	# [<bool>]
        #Option     "ConnectorTable"     	# <str>
        #Option     "DefaultConnectorTable" 	# [<bool>]
        #Option     "DefaultTMDSPLL"     	# [<bool>]
        #Option     "TVDACLoadDetect"    	# [<bool>]
        #Option     "ForceTVOut"         	# [<bool>]
        #Option     "TVStandard"         	# <str>
        #Option     "IgnoreLidStatus"    	# [<bool>]
        #Option     "DefaultTVDACAdj"    	# [<bool>]
        #Option     "Int10"              	# [<bool>]
        #Option     "EXAVSync"           	# [<bool>]
        #Option     "ATOMTVOut"          	# [<bool>]
        #Option     "R4xxATOM"           	# [<bool>]
        #Option     "ForceLowPowerMode"  	# [<bool>]
        #Option     "DynamicPM"          	# [<bool>]
	Identifier  "Card0"
	Driver      "radeon"
	VendorName  "ATI Technologies Inc"
	BoardName   "Radeon Mobility M7 LW [Radeon Mobility 7500]"
	BusID       "PCI:1:0:0"
EndSection

Section "Screen"
	Identifier "Screen0"
	Device     "Card0"
	Monitor    "Monitor0"
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
 
```

I have generated the xorg.conf file from root. This is my default settings.

---

### Post by hwttdz on 2009-12-10
Why not try backing it up to ~ and then removing it and letting it regenerate.  See what the system thinks, as it has all sorts of information that we don't like which version of the OS, which version of X and which video card/cpu you have.  the system usually does a pretty good job.

---

### Post by domagoj91 on 2009-12-10
> **hwttdz said:**
> Why not try backing it up to ~ and then removing it and letting it regenerate.  See what the system thinks, as it has all sorts of information that we don't like which version of the OS, which version of X and which video card/cpu you have.  the system usually does a pretty good job.

It didn't, this is the system created one.


Regards Domagoj!

---

### Post by domagoj91 on 2009-12-11
Need help with this FAST...

---

### Post by Draygera on 2009-12-11
If you have ubuntu 9.10, use this guide!!! It worked great for me.

[http://www.osguides.net/operation-systems/217-how-to-create-xorgconf-in-ubuntu-910.html](http://www.osguides.net/operation-systems/217-how-to-create-xorgconf-in-ubuntu-910.html)

Just make sure you've uninstalled your ATI (not sure about Nvidia) propriety drivers such as FGLRX before running the commands, or else you'll get a segmentation fault error. And if your drivers don't work after installing them, delete your xorg.conf and uninstall jockey-common and jockey-gtk and then rinse and redo; this solves some other problems you could get.

```


sudo rm -rv /etc/X11/xorg.conf


```

For deleting your xorg.conf.

---

### Post by domagoj91 on 2009-12-11
> **Draygera said:**
> If you have ubuntu 9.10, use this guide!!! It worked great for me.

[http://www.osguides.net/operation-systems/217-how-to-create-xorgconf-in-ubuntu-910.html](http://www.osguides.net/operation-systems/217-how-to-create-xorgconf-in-ubuntu-910.html)

Just make sure you've uninstalled your ATI (not sure about Nvidia) propriety drivers such as FGLRX before running the commands, or else you'll get a segmentation fault error. And if your drivers don't work after installing them, delete your xorg.conf and uninstall jockey-common and jockey-gtk; this solved some other problems you could get.

i am getting segmentation error but i haven't installed FGLRX drivers. I will try this thanks...

---

### Post by Draygera on 2009-12-11
Do you have Ati or Nvidia? If you installed any of the pre-release Karmics, Fglrx drivers are automatically installed. Check your Synaptic about it. If they are installed, uninstall and you might stop getting the seg fault. Give me a shout as soon as possible.

Edit: Of course because you haven't installed any drivers, that could be your problem too. LOL. You could just try installing them by going to System->Administration->Hardware Drivers->Activate and reboot after it's done. If that doesn't work than do what the guide tells you.

---

### Post by domagoj91 on 2009-12-11
> **Draygera said:**
> Do you have Ati or Nvidia? If you installed any of the pre-release Karmics, Fglrx drivers are automatically installed. Check your Synaptic about it. If they are installed, uninstall and you might stop getting the seg fault. Give me a shout as soon as possible.

Edit: Of course because you haven't installed any drivers, that could be your problem too. LOL. You could just try installing them by going to System->Administration->Hardware Drivers->Activate and reboot after it's done. If that doesn't work than do what the guide tells you.

I've done like you sayed but ther is no change. Oh yes I do not have System-Administration-Hardware Drivers option. I've installed latest Drivers ant never installed FGLRX. I've alredy done this guide before I post this thread, appaerently. I am ATI M7500 radeon user.

---

### Post by Draygera on 2009-12-12
Just got back from work and hopefully you got my PM. If it doesn't work, then I'm completely dumbfounded.

---

