---
title: "Poor Performance On Pentium 4 Machine"
date: 2011-08-04
forum: General Help
---

### Post by dodle on 2011-08-04
I just installed Ubuntu 10.04 on a laptop that was given to me. It is having a lot of lag issues, especially when playing videos and visiting websites using flash. It's an Intel Pentium 4 2.4GHz machine. I think that it should perform better because I had used and AMD Sempron 2.0GHz machine with Ubuntu before and video playback was much better than this. I'm thinking that my problem is the graphics card driver. Here is the card that this machine has:

```
:~$ lspci | grep Radeon
01:05.0 VGA compatible controller: ATI Technologies Inc Radeon IGP 330M/340M/350M
```

The AMD machine was using a VIA graphics chipset.

I used the command "Xorg -configure" to create a xorg.conf file, hoping that might help. But it didn't. Here it is:

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
	Load  "record"
	Load  "dri"
	Load  "extmod"
	Load  "glx"
	Load  "dbe"
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
	Identifier   "Monitor0"
	VendorName   "Monitor Vendor"
	ModelName    "Monitor Model"
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
        #Option     "CustomEDID"         	# [<str>]
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
        #Option     "NewPLL"             	# [<bool>]
        #Option     "ZaphodHeads"        	# <str>
	Identifier  "Card0"
	Driver      "radeon"
	VendorName  "ATI Technologies Inc"
	BoardName   "Radeon IGP 330M/340M/350M"
	BusID       "PCI:1:5:0"
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

Is there any tweaking that I can do in the xorg.conf that might help? I don't know which of those options I should set. I also tried changing the driver to "ati" but that did nothing.

**----- EDIT -----**
I found some info for settings with "man radeon", I'm going to try some of those out.

---

### Post by ninjaaron on 2011-08-04
Installing the "flash aid" extension in Firefox and getting the latest version improves Flash's performance in Ubuntu immensely.  I don't know if that will fix the problem, but it will at least help.

---

### Post by Mark Phelps on 2011-08-04
There are no new Linux video drivers for that chip.  AMD dropped Linux driver for that years ago.  The open-source driver, which is installed by default, is what's available now.

---

### Post by .... on 2011-08-04
Neither of those video chips has hardware video acceleration, so it comes down to the CPU speed. A Sempron 2.0GHz is probably faster than a P4 2.4GHz, especially if it's a S754 or AM2 Sempy.

---

### Post by dodle on 2011-08-04
I'm wondering if my problem might be a heat issue. This laptop has 3 fans but I have only ever seen 1 spinning.

---

### Post by Mark Phelps on 2011-08-04
That's NOT a heat issue -- fans not spinning.  A heat issues is more readily seen when the fans, which used to be idle in some other OS, are now spinning all or nearly all of the time.

As long as the PC doesn't feel overly warm and the fans are not spinning a lot, count yourself lucky that you don't have a heat issue.

---

### Post by dodle on 2011-08-04
I was just thinking that maybe the fans weren't working, thereby causing the system to heat up.

---

### Post by .... on 2011-08-04
When was the last time this was thing was opened up and dusted out? Do you monitor the temps at all?

---

### Post by dodle on 2011-08-04
I've got it opened up now and all the vents are clogged with dust and lint. I was surprised to find a socket 478 processor in this thing. That and the Intel socket 775 are the two processors I am most familiar with. They used to be used in a lot of desktops. I'm also looking for bulging capacitors or anything else suspicious but haven't found anything yet. The CPU looks fine and the fan connectors appear to be OK. It looks like it has good ventilation. I have to say, this is the easiest laptop I've ever taken apart.

I feel like this laptop should definitely perform better. I had a 2.6GHz 478 desktop that was blazing fast with Ubuntu a few years ago. The big difference was it had a dedicated 256MB GeForce graphics card.

---

### Post by dodle on 2011-08-04
After cleaning out the dust and putting some new thermal grease on the CPU it seems to perform a little better. The DVD playback still isn't perfect. But streaming flash looks better.

```
:~$ hdparm /dev/dvd

/dev/dvd:
 HDIO_DRIVE_CMD(identify) failed: Bad address
 IO_support    =  1 (32-bit)
 readonly      =  0 (off)
 readahead     = 256 (on)
 HDIO_GETGEO failed: Inappropriate ioctl for device
```

**NOTE:** There were no left over screws after I put it back together. This is a first for me :)

**----- EDIT -----**
Streaming flash and DVD playback both have issues when in fullscreen, choppy video.

---

### Post by pqwoerituytrueiwoq on 2011-08-04
if your system has sensors we can get the temperature
```
sudo apt-get install sensors
sudo sensors-detect
sensors
```

---

### Post by dodle on 2011-08-04
No sensors were detected, but a gnome applet tells me that the CPU is running around 47°C. I think that is a decent temperature.

---

### Post by wildmanne39 on 2011-08-05
Hi, yes that temp should be ok.

How much memory does this laptop Have?

---

### Post by dodle on 2011-08-06
It only has 512mb, this machine can only be upgraded to a max of 1gb... bleh!

I've decided to put XP back on this machine. It definitely runs it better. Looks like I won't have a Linux machine until I can get my other laptop fixed :mad:

**----- EDIT ----- **
Actually, I may put Lubuntu on it. I ran that on my Sempron machine and it handled it okay. Couldn't get bluetooth to work though.

**Note:** This laptop doesn't have USB 2.0 ](*,)... but it does have a floppy drive :-s

---

### Post by wildmanne39 on 2011-08-06
Hi, good luck.

---

### Post by dodle on 2011-08-06
Lubuntu seems to be running decently. DVD playback appears to be better so far. But if I plan to use this computer for any length of time I should probably upgrade the RAM to max.

---

### Post by wildmanne39 on 2011-08-06
Hi, I agree more memory will help.

---

