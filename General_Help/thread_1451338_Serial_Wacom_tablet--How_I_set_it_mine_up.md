---
title: "Serial Wacom tablet--How I set it mine up"
date: 2010-04-10
forum: General Help
---

### Post by luminol on 2010-04-10
[SIZE="4"]How I Set Up a Serial Wacom Tablet In 10 Mostly-Easy Steps[/SIZE]
----
NOTE: I used Linux Mint 8 Helena KDE, which is based on Karmic. The same principles should translate to other *buntus (although I couldn't find wacom-tools in the repos for Lucid).

UPDATE: Tried with Lucid Beta 1, no luck.

UPDATE: The Xorg defaults appear to break KDE, with kwin crashing, no borders on windows, assorted ugliness. The solution is apparently to remove the proprietary fglrx drivers and replace them with the open-source Radeon ones, through Synaptic or, in Terminal:

sudo apt-get remove xorg-driver-fglrx fglrx-amdcccle fglrx-modaliases

and

sudo apt-get install libdrm-radeon1 xserver-xorg-video-radeonhd xserver-xorg-video-radeon xserver-xorg-video-ati

There's supposed to be a performance hit with these drivers, but I can't tell. I'm using my on-board ATI Radeon X1200 because the fan melted in my Nvidia card, so it all looks slower. With the new ATI drivers I went from 25 sec. from Grub to Desktop, to about a minute & a half.

It's either a fast boot & faster 3D or no Wacom tablet. Dang.

---

Also, this was all done in a Live CD session (I'm posting this from it), so you could potentially try out a (Ubuntu/Debian-based) distro before installing to see if it would work with your pad.
---
It's not as bad as it looks. Ten easy steps, I promise.
---
First off, bookmark this page. Print these instructions out to Step #6 or write them down. We'll be stopping and re-starting the window manager during this adventure. Remain calm.

1) In terminal, sudo apt-get install wacom-tools (if you haven't already)

2) In terminal: xxd /dev/ttyS0. Touch the stylus to the pad and you should get many, many lines of garbled text on the screen. If not, hit Ctrl-C and try xxd /dev/ttyS1. Work your way up until you get a response.  

(NOTE: My Intuous 12x12 is hooked up through a serial-to-usb adapter, so it's: xxd /dev/ttyUSB0. It still sets up as a serial connection even though it goes through USB. I don't get it either.)

3) In Terminal: sudo stop kdm (if you're using KDE; if you're using Gnome, sudo stop gdm).

4) At the command line: Xorg -configure (yes, that is a capital X). Note where your xorg*.new file is written. On mine, it went to the /home/mint folder. 

5) In terminal: sudo cp <the location of your newly created xorg*.new file> /etc/X11/xorg.conf. In my case: sudo cp /home/mint/xorg.conf.new /etc/X11/xorg.conf

6) sudo start kdm (or gdm, in Gnome), because editing this next bit in the CLI is a pain in the ****.

7) In Terminal: kdesudo kate /etc/X11/xorg.conf (for Gnome, gksudo gedit /etc/X11/xorg.conf)

8) Now, we edit. See those blocks that begin with Section "InputDevice" ? Find the last one and paste this underneath it:

Section "InputDevice"
  Driver        "wacom"
  Identifier    "stylus"
  Option        "Device"        "/dev/ttyS0"          # SERIAL ONLY
  Option        "Device"        "/dev/input/wacom"    # USB ONLY
  Option        "Type"          "stylus"
  Option        "USB"           "on"                  # USB ONLY
  Option        "ForceDevice"   "ISDV4"               # Serial Tablet PC ONLY
EndSection

Section "InputDevice"
  Driver        "wacom"
  Identifier    "eraser"
  Option        "Device"        "/dev/ttyS0"          # SERIAL ONLY
  Option        "Device"        "/dev/input/wacom"    # USB ONLY
  Option        "Type"          "eraser"
  Option        "USB"           "on"                  # USB ONLY
  Option        "ForceDevice"   "ISDV4"               # Serial Tablet PC ONLY
EndSection

Section "InputDevice"
  Driver        "wacom"
  Identifier    "cursor"
  Option        "Device"        "/dev/ttyS0"          # SERIAL ONLY
  Option        "Device"        "/dev/input/wacom"    # USB ONLY
  Option        "Type"          "cursor"
  Option        "USB"           "on"                  # USB ONLY
  Option        "ForceDevice"   "ISDV4"               # Serial Tablet PC ONLY
EndSection

# This section is for Intuos3, CintiqV5, Graphire4, or Bamboo
Section "InputDevice"
  Driver        "wacom"
  Identifier    "pad"
  Option        "Device"        "/dev/ttyS0"          # SERIAL ONLY
  Option        "Device"        "/dev/input/wacom"    # USB ONLY
  Option        "Type"          "pad"
  Option        "USB"           "on"                  # USB ONLY
EndSection

# This section is for the TabletPC that supports touch
Section "InputDevice"
  Driver        "wacom"
  Identifier    "touch"
  Option        "Device"        "/dev/ttyS0"          # SERIAL ONLY
  Option        "Device"        "/dev/input/wacom"    # USB ONLY
  Option        "Type"          "touch"
  Option        "ForceDevice"   "ISDV4"               # Serial Tablet PC ONLY
  Option        "USB"           "on"                  # USB ONLY
EndSection

Change all the instances of "dev/ttyS0" to whatever address your pad is on (in my case /dev/ttyUSB0). Find and Replace is handy for this.

We're working with a serial tablet, so comment out (#) all the lines that read:

  Option        "USB"           "on"                  # USB ONLY

and

  Option        "ForceDevice"   "ISDV4"               # Serial Tablet PC ONLY

At the top, in Section "ServerLayout", paste the following above the EndSection line:

InputDevice    "stylus"    "SendCoreEvents"
        InputDevice    "eraser"    "SendCoreEvents"
        InputDevice    "cursor"    "SendCoreEvents"    # For non-LCD tablets only
	InputDevice    "touch"     "SendCoreEvents"    # Only a few TabletPCs support this type
        InputDevice    "pad"   # For Intuos3/CintiqV5/Graphire4/Bamboo tablets

My complete xorg.conf is at the bottom of this post.

9) In terminal: sudo stop kdm (or gdm for Gnome). At the command line: sudo start kdm (or gdm). Does the tablet work? Great. No? Check xorg.conf for typos. I gutted an install once only to discover I'd left out a ".

10) Bask in the glory of a job well done.
---
As promised, xorg.conf:

```
Section "ServerLayout"
	Identifier     "X.org Configured"
	Screen      0  "Screen0" 0 0
	InputDevice    "Mouse0" "CorePointer"
	InputDevice    "Keyboard0" "CoreKeyboard"
	InputDevice    "stylus"    "SendCoreEvents"
        InputDevice    "eraser"    "SendCoreEvents"
        InputDevice    "cursor"    "SendCoreEvents"    # For non-LCD tablets only
	InputDevice    "touch"     "SendCoreEvents"    # Only a few TabletPCs support this type
        InputDevice    "pad"   # For Intuos3/CintiqV5/Graphire4/Bamboo tablets
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
	Load  "dbe"
	Load  "dri"
	Load  "dri2"
	Load  "extmod"
	Load  "glx"
	Load  "record"
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

Section "InputDevice"
  Driver        "wacom"
  Identifier    "stylus"
  Option        "Device"        "/dev/ttyUSB0"          # SERIAL ONLY
  #Option        "Device"        "/dev/input/wacom"    # USB ONLY
  Option        "Type"          "stylus"
  #Option        "USB"           "on"                  # USB ONLY
  #Option        "ForceDevice"   "ISDV4"               # Serial Tablet PC ONLY
EndSection

Section "InputDevice"
  Driver        "wacom"
  Identifier    "eraser"
  Option        "Device"        "/dev/ttyUSB0"          # SERIAL ONLY
  #Option        "Device"        "/dev/input/wacom"    # USB ONLY
  Option        "Type"          "eraser"
  #Option        "USB"           "on"                  # USB ONLY
  #Option        "ForceDevice"   "ISDV4"               # Serial Tablet PC ONLY
EndSection

Section "InputDevice"
  Driver        "wacom"
  Identifier    "cursor"
  Option        "Device"        "/dev/ttyUSB0"          # SERIAL ONLY
  #Option        "Device"        "/dev/input/wacom"    # USB ONLY
  Option        "Type"          "cursor"
  #Option        "USB"           "on"                  # USB ONLY
  #Option        "ForceDevice"   "ISDV4"               # Serial Tablet PC ONLY
EndSection

# This section is for Intuos3, CintiqV5, Graphire4, or Bamboo
Section "InputDevice"
  Driver        "wacom"
  Identifier    "pad"
  Option        "Device"        "/dev/ttyUSB0"          # SERIAL ONLY
  #Option        "Device"        "/dev/input/wacom"    # USB ONLY
  Option        "Type"          "pad"
  #Option        "USB"           "on"                  # USB ONLY
EndSection

# This section is for the TabletPC that supports touch
Section "InputDevice"
  Driver        "wacom"
  Identifier    "touch"
  Option        "Device"        "/dev/ttyUSB0"          # SERIAL ONLY
  #Option        "Device"        "/dev/input/wacom"    # USB ONLY
  Option        "Type"          "touch"
#  #Option        "ForceDevice"   "ISDV4"               # Serial Tablet PC ONLY
  #Option        "USB"           "on"                  # USB ONLY
EndSection


Section "Monitor"
	#DisplaySize	  380   280	# mm
	Identifier   "Monitor0"
	VendorName   "RDS"
	ModelName    "XL-2"
	HorizSync    30.0 - 108.0
	VertRefresh  50.0 - 152.0
	Option	    "DPMS"
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
	BoardName   "RS690 [Radeon X1200 Series]"
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

---

### Post by JAKEOTR on 2010-04-10
But do you have full functionality? I have the tablet working but the problem is the stylus lagging. Everything else works but the stylus lags until you touch it to the pad.

---

### Post by luminol on 2010-04-10
Try Terminal: wacomcpl, and adjust the tracking for the cursor. The default settings are a little sluggish. Sounds like the stylus is okay, though.

---

### Post by JAKEOTR on 2010-04-12
So youre saying yours is working perfectly, no issues, using this how-to?

---

### Post by omskates on 2010-04-15
Lots of help from Favux on this  [http://ubuntuforums.org/showthread.php?t=1038949](http://ubuntuforums.org/showthread.php?t=1038949)  

I was very fortunate with my Fujitsu Lifebook T series and Linux Mint 8 Helena.  After wacom tools installed and a driver for rotation & buttons I now have perfect wacom pen and everything works smoothly, no custom xorg editing needed for me :)

---

### Post by fragos on 2010-04-15
My Wacom Graphire4 is requires no configuration with Ubuntu 9.10 nor did it with 9.04. Although xorg.conf was required in the past and still can be used for configuration it rarely is these days.

---

### Post by luminol on 2010-05-07
> **JAKEOTR said:**
> So youre saying yours is working perfectly, no issues, using this how-to?

So far, so good. In fact, I had to run through it again when I got my old Nvidia card running (zip-tie + case cooling fan over the heat sink FTW). The new xorg.conf looks like:

```
Section "ServerLayout"
	Identifier     "X.org Configured"
	InputDevice    "Mouse0" "CorePointer"
	InputDevice    "Keyboard0" "CoreKeyboard"
	InputDevice    "stylus"    "SendCoreEvents"
        InputDevice    "eraser"    "SendCoreEvents"
        InputDevice    "cursor"    "SendCoreEvents"    # For non-LCD tablets only
	InputDevice    "touch"     "SendCoreEvents"    # Only a few TabletPCs support this type
        InputDevice    "pad"   # For Intuos3/CintiqV5/Graphire4/Bamboo tablets
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

Section "InputDevice"
  Driver        "wacom"
  Identifier    "stylus"
  Option        "Device"        "/dev/ttyUSB0"          # SERIAL ONLY
  Option        "Device"        "/dev/input/wacom"    # USB ONLY
  Option        "Type"          "stylus"
  #Option        "USB"           "on"                  # USB ONLY
  #Option        "ForceDevice"   "ISDV4"               # Serial Tablet PC ONLY
EndSection

Section "InputDevice"
  Driver        "wacom"
  Identifier    "eraser"
  Option        "Device"        "/dev/ttyUSB0"          # SERIAL ONLY
  Option        "Device"        "/dev/input/wacom"    # USB ONLY
  Option        "Type"          "eraser"
  Option        "USB"           "on"                  # USB ONLY
  #Option        "ForceDevice"   "ISDV4"               # Serial Tablet PC ONLY
EndSection

Section "InputDevice"
  Driver        "wacom"
  Identifier    "cursor"
  Option        "Device"        "/dev/ttyUSB0"          # SERIAL ONLY
  Option        "Device"        "/dev/input/wacom"    # USB ONLY
  Option        "Type"          "cursor"
  Option        "USB"           "on"                  # USB ONLY
  #Option        "ForceDevice"   "ISDV4"               # Serial Tablet PC ONLY
EndSection

# This section is for Intuos3, CintiqV5, Graphire4, or Bamboo
Section "InputDevice"
  Driver        "wacom"
  Identifier    "pad"
  Option        "Device"        "/dev/ttyUSB0"          # SERIAL ONLY
  Option        "Device"        "/dev/input/wacom"    # USB ONLY
  Option        "Type"          "pad"
  #Option        "USB"           "on"                  # USB ONLY
EndSection

# This section is for the TabletPC that supports touch
Section "InputDevice"
  Driver        "wacom"
  Identifier    "touch"
  Option        "Device"        "/dev/ttyUSB0"          # SERIAL ONLY
  Option        "Device"        "/dev/input/wacom"    # USB ONLY
  Option        "Type"          "touch"
  Option        "ForceDevice"   "ISDV4"               # Serial Tablet PC ONLY
  #Option        "USB"           "on"                  # USB ONLY
EndSection

Section "Monitor"
	#DisplaySize	  380   280	# mm
	Identifier   "Monitor0"
	VendorName   "RDS"
	ModelName    "XL-2"
	HorizSync    30.0 - 108.0
	VertRefresh  50.0 - 152.0
	Option	    "DPMS"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	DefaultDepth	24
EndSection

Section "Module"
	Load	"glx"
EndSection

Section "Device"
	Identifier	"Default Device"
	Driver	"nvidia"
	Option	"NoLogo"	"True"
EndSection
```

I had some typos in it at first and had to look at /var/log/Xorg.0.log a few times to figure out why KDE wasn't coming up.

The only issue I could see is, I'm running all this on a new-ish Athlon dual-core (Acer AM-1100 w/3gb RAM), so an older machine may lag pretty hard.

---

### Post by luminol on 2010-05-07
[SIZE="3"]And, to all those whose tablets plugged into a USB port and just worked, know this:

I hope you spill a Mountain Dew on it.[/SIZE] :lolflag:

---

### Post by luminol on 2010-07-04
But, seriously, folks...

Here's another approach. Haven't tested it out, but it's fewer steps and it supposedly fixes any latency problems.

[URL="http://blog.philpem.me.uk/?p=280"]
Making a Wacom A6 ArtPad (KT-0405-R) work on Ubuntu 9.04[/URL]

I upgraded to Lucid & am still dead in the water.
The frustrating part is being able to enter ```
sudo xxd /dev/ttyUSBO
``` and see output, same as if I entered ```
sudo xxd /dev/input/event4
``` and moved the mouse or ```
sudo xxd /dev/input/event3
``` and typed on the keyboard. Why do the latter two work and the first one not? Grr.

---

### Post by Favux on 2010-07-04
Hi luminol,

The xf86-input-wacom driver that comes with Lucid/Xserver 1.7 does not support serial tablets yet.  You can try patching it to get serial tablet support.  A few have succeeded.  See near the top of the [linuxwacom HOw TO]("http://ubuntuforums.org/showpost.php?p=6546012&postcount=1").

---

### Post by luminol on 2010-07-15
Couldn't get the patches to apply to the latest git clone. I'm done.

The last Ubuntu version that worked with my tablet was Jaunty. I'm going back to that.

---

### Post by Favux on 2010-07-15
Hi luminol,

You could try the 0.10.7 tar instead of the latest git clone.  The patches should still work on it.  They just merged some fairly significant changes to the serial stuff which is probably why the patches didn't work.

But going back to an older release makes sense too.

---

### Post by luminol on 2010-07-22
Installed Karmic and have things working. Kind of.

I disabled "show boot splash" and "show text during boot" through Startup Manager. Otherwise I would get a black, unresponsive screen until I unplugged the tablet.

The tablet doesn't still doesn't work until I either

(1) Hit CTRL-ALT-Backspace and log back in, or

(2) Open up Terminal and type in sudo /etc/init.d/gdm stop (and then start).

I'll go through xorg.conf and check for errors and look in /var/log while I wait for that shiny graphical tablet installer in 10.10 or Maverick.:D

Thanks for the help, Fauvx & everybody.

---

### Post by crparis on 2010-11-10
Good day, everyone!

While my tablet isn't working, I feel like I'm really close and need to ask the community to see if anyone knows what I need to do to get the last 5% of this done.

- I grabbed xf86-input-wacom-0.10.8
- configure
- make
- make install
- tested the tablet output with xxd /dev/ttyUSB0

No problem so far--woot!

- start X, tablet not working
- check Xorg.0.log for clues

```

[  1783.746] (II) LoadModule: "wacom"
[  1783.747] (II) Loading /usr/lib/xorg/modules/input/wacom_drv.so
[  1783.748] (II) Module wacom: vendor="X.Org Foundation"
[  1783.748] 	compiled for 1.8.99.905, module version = 0.10.8
[  1783.748] 	Module class: X.Org XInput Driver
[  1783.748] 	ABI class: X.Org XInput driver, version 11.0

# module is loading fine!

[  1784.551] (**) Option "Device" "/dev/ttyUSB0"
[  1784.586] (**) Option "StopBits" "1"
[  1784.586] (**) Option "DataBits" "8"
[  1784.586] (**) Option "Parity" "None"
[  1784.586] (**) Option "Vmin" "1"
[  1784.586] (**) Option "Vtime" "10"
[  1784.586] (**) Option "FlowControl" "Xoff"
[  1784.586] (**) Option "SendCoreEvents"
[  1784.586] (**) stylus: always reports core events
[  1784.586] (WW) stylus: Touch option can only be set by a touch tool.
[  1784.586] (WW) stylus: Touch gesture option can only be set by a touch tool.
[  1787.851] (WW) stylus: Waited too long for answer (failed after 3 tries).
[  1787.852] (WW) stylus: Query failed with 38400 baud. Trying 19200.
[  1791.116] (WW) stylus: Waited too long for answer (failed after 3 tries).
[  1794.369] (WW) stylus: Waited too long for answer (failed after 3 tries).
[  1794.369] (II) stylus: serial tablet id 0x0.
[  1794.503] (II) UnloadModule: "wacom"
[  1794.503] (EE) PreInit returned NULL for "stylus"
```

I'm not sure why it's timing out / waiting too long, as the tablet talks on 38400 baud no problem:

```

$ ./isdv4-serial-debugger -b 38400 /dev/ttyUSB0
TABLET: version: 15480
TABLET: x max: 61955 y max 515
TABLET: tilt_x max: 120 tilt_y max 0
TABLET: pressure max: 120
TOUCH version: 16504
TOUCH x max: 512 y max 0
TOUCH panel resolution: 120
TOUCH capacity resolution: 248
TOUCH sensor id: 0
```

I'm stumped!

Thanks for any assistance any of you may lend!!  :-)

--Clinton

---

### Post by Favux on 2010-11-10
Hi Clinton,

What Wacom serial tablet do you have?

I gather you are in Maverick (10.10).  Is that correct?

Support was dropped for serial tablets in xf86-input-wacom due to lack of developer resources at the LWP.  However some patches were made to support serial tablets by some coders with serial tablets.  Unfortunately they only work up to and including xf86-input-wacom 0.10.6 (because development stopped), which doesn't compile on Maverick.  Fortunately just a couple of days ago thorwil discovered how to get it to compile.

See brief discussion with links at the [linuxwacom HOW TO]("http://ubuntuforums.org/showpost.php?p=6546012&postcount=1") near the top.

---

### Post by crparis on 2010-11-12
> **Favux said:**
> Hi Clinton,

What Wacom serial tablet do you have?

I gather you are in Maverick (10.10).  Is that correct?

Support was dropped for serial tablets in xf86-input-wacom due to lack of developer resources at the LWP.  However some patches were made to support serial tablets by some coders with serial tablets.  Unfortunately they only work up to and including xf86-input-wacom 0.10.6 (because development stopped), which doesn't compile on Maverick.  Fortunately just a couple of days ago thorwil discovered how to get it to compile.

See brief discussion with links at the [linuxwacom HOW TO]("http://ubuntuforums.org/showpost.php?p=6546012&postcount=1") near the top.

You must be psychic--you identified my situation perfectly!

Looked at the tutorial and got everything going--thanks so much for pointing me in the right direction!!

--Clinton

---

### Post by fra.1711 on 2010-12-25
Hi i have the same problem of crparis (my xorg.log give the same message and isdv4-serial-debugger too) but i'm on lucid.
how can i fix the problem?

---

### Post by Favux on 2010-12-26
Hi fra.1711,

Welcome to Ubuntu forums!

You should just need to download the 0.10.6 xf86-inpu-wacom tar and apply the serial patches to it and then compile.  Since you are in Lucid you shouldn't need to add thorwil's patch as 0.10.6 should compile in the 2.6.32 kernel just fine.

---

