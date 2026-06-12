---
title: "hoary. nvidia xorg dual display config"
date: 2005-03-15
forum: General Help
---

### Post by themole on 2005-03-15
Hi

I have been trying in vain to get dual displays to work in hoary.

i had it working in warty, but i have since done a reinstall and forget what settign is used.

Primary display: Dell E171FP LCD
secondary display: Dell M782P CRT

both are connected to my Nvidia GeForce FX 5200, which has a DVI connector which splits into two vga.

i presume i need to use twin view, i want a spanned desktop.

here is my xorg.conf file:
Section "Files"
	FontPath	"unix/:7100"			# local font server
	# if the local font server has problems, we can fall back on these
	FontPath	"/usr/lib/X11/fonts/misc"
	FontPath	"/usr/lib/X11/fonts/cyrillic"
	FontPath	"/usr/lib/X11/fonts/100dpi/:unscaled"
	FontPath	"/usr/lib/X11/fonts/75dpi/:unscaled"
	FontPath	"/usr/lib/X11/fonts/Type1"
	FontPath	"/usr/lib/X11/fonts/CID"
	FontPath	"/usr/lib/X11/fonts/100dpi"
	FontPath	"/usr/lib/X11/fonts/75dpi"
        # paths to defoma fonts
	FontPath	"/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
	FontPath	"/var/lib/defoma/x-ttcidfont-conf.d/dirs/CID"
EndSection

Section "Module"
	Load	"bitmap"
	Load	"dbe"
	Load	"ddc"
	Load	"dri"
	Load	"extmod"
	Load	"freetype"
	Load	"glx"
	Load	"int10"
	Load	"record"
	Load	"type1"
	Load	"vbe"
EndSection

Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"keyboard"
	Option		"CoreKeyboard"
	Option		"XkbRules"	"xorg"
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
	Identifier	"NVIDIA Corporation NV34 [GeForce FX 5200]"
	Driver		"nv"
	BusID		"PCI:1:0:0"
	Option	"TwinView" "on" 
	Option	"MetaModes"  "1280x1024,1600x1200; 1280x1024,1240x768"
	Option	"SecondMonitorHorizSync" "30-85"
	Option	"SecondMonitorVertRefresh" "50-160"
	Option 	"TwinViewOrientation"	"RightOf"
EndSection

Section "Monitor"
	Identifier	"Generic Monitor"
	Option		"DPMS"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"NVIDIA Corporation NV34 [GeForce FX 5200]"
	Monitor		"Generic Monitor"
	DefaultDepth	24
	SubSection "Display"
		Depth		1
		Modes		"1280x1024" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1280x1024" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1280x1024" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1280x1024" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1280x1024" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1280x1024" "1024x768" "800x600" "640x480"
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


everything is from the default config file, except the twinview stuff.

using this file i only get the primary monitor to display, the other one has flashing colours on it.

any help would be appreciated.

---

### Post by c_dog on 2005-03-15
The open source "nv" driver does not have twinview capabiliites. You will need to change the "nv" driver in the Section "Device" to  "nvidia"  and have nvidia's driver installed by either installing the nvidia debs or compiling the driver module from the script available on nviidia's site.

c_dog

---

### Post by themole on 2005-03-15
so the nvidia-glx package i installed using synaptic cannot support twinview?

---

### Post by minuo on 2005-03-15
It should, but the driver listed in your xorg.conf should be 'nvidia', not 'nv'.

---

### Post by c_dog on 2005-03-15
Hoary installs the open source "nv" driver written by Mark Vojkovich by default. The nvidia-glx driver is in the "restricted" repositories because is bulit with the proprietory Nvidia corp supplied driver binaries.
c_dog

---

### Post by themole on 2005-03-16
when i changed from nv to nvidia the x server wouldn't start

---

### Post by tennessee@tennessee.id.au on 2005-03-31
Hey, I have just been wrestling with nvidia under hoary. I upgraded and happily used it for months until I had to reboot, the WHOA!

Here is what you have to do :

apt-get remove nvidia-kernel-common
apt-get remove nvidia-glx
apt-get remove anything else you might have

rm /etc/rc?.d/*nvidia-glx
/etc/init.d/gdm stop

change your xorg.conf to use the "nv" driver, or use dpkg-reconfigure xserver-xorg to get a text UI wizard.

That will completely remove the nvidia stuff from your system. You can't use it with hoary as far as I can tell. Which means no twinview. But at least this way you can get X back.

---

### Post by Whiffle on 2005-03-31
Ummm nvidia works great over here...twinview and all..  under hoary.  geforce4ti4200.  Only thing that doesn't work is Composite w/ twinview.  Composite works w/o twinview though, dunno why.

I have nvidia-glx, nvidia-kernel-common, and nvidia-settings installed (settings isn't necessary).  Then in /etc/modules I added "nvidia" to the bottom of the list.  

here is my xorg conf:  You'll want to substitute in your values.

```

# XF86Config-4 (XFree86 X Window System server configuration file)
#
# This file was generated by dexconf, the Debian X Configuration tool, using
# values from the debconf database.
#
# Edit this file with caution, and see the XF86Config-4 manual page.
# (Type "man XF86Config-4" at the shell prompt.)
#
# This file is automatically updated on xserver-xfree86 package upgrades *only*
# if it has not been modified since the last upgrade of the xserver-xfree86
# package.
#
# If you have edited this file but would like it to be automatically updated
# again, run the following commands as root:
#
#   cp /etc/X11/XF86Config-4 /etc/X11/XF86Config-4.custom
#   md5sum /etc/X11/XF86Config-4 >/var/lib/xfree86/XF86Config-4.md5sum
#   dpkg-reconfigure xserver-xfree86

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
	Load	"GLcore"
	Load	"bitmap"
	Load	"dbe"
	Load	"ddc"
	Load	"dri"
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
	Option		"XkbModel"	"pc104"
	Option		"XkbLayout"	"us"
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
	Identifier	"NVIDIA"
	Driver		"nvidia"
	BusID		"PCI:1:0:0"
        Option          "RenderAccel"           "true"
        Option          "NvAGP"                 "1"
        Option 		"AllowGLXWithComposite" "true"

EndSection

Section "Monitor"
	Identifier	"Viewsonic"
	HorizSync	30-86
	VertRefresh	50-180
	Option		"DPMS"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"NVIDIA"
	Monitor		"Viewsonic"
	DefaultDepth 	24
	Option          "TwinView"              "true"
	Option          "SecondMonitorHorizSync" "30-70"
        Option          "SecondMonitorVertRefresh" "50-120"
	Option          "MetaModes" "1152x864, 1152x864; 1152x864, 1152x864;"
	Option          "TwinViewOrientation" "RightOf"

	Subsection "Display"
		Depth 24
		Modes "1152x864"
		ViewPort 0 0 
	EndSubsection
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		"Default Screen"
	InputDevice	"Generic Keyboard"
	InputDevice	"Configured Mouse"
EndSection

#Section "DRI"
#	Mode	0666
#EndSection

Section "Extensions"
#	Option 	"Composite" "Enable"
	Option 	"Composite" "Disable"
EndSection

```

---

### Post by PhatSOB on 2005-04-09
ok guys I am a total noob to linux and I have 2 monitors connected to my 6800GT.  Only one of them displays anything.  I have looked through several threads and I can't follow whatI am supposed to do. any of the files that I am supposed to change are Read only.  So I need a little help.

#1 how do I change these files that need to be changed?

#2 could some one walk me through getting my 2nd display working or atleast switch which monitor is the default?

#3 I tried to download the newest nvidia driver but I don't know how to run this?

some help would be great, thanks

---

### Post by tennessee@tennessee.id.au on 2005-04-12
[QUOTE=Whiffle]Ummm nvidia works great over here...twinview and all..  under hoary.  geforce4ti4200.  Only thing that doesn't work is Composite w/ twinview.  Composite works w/o twinview though, dunno why.

I have nvidia-glx, nvidia-kernel-common, and nvidia-settings installed (settings isn't necessary).  Then in /etc/modules I added "nvidia" to the bottom of the list.  

here is my xorg conf:  You'll want to substitute in your values.

```

# XF86Config-4 (XFree86 X Window System server configuration file)
#
# This file was generated by dexconf, the Debian X Configuration tool, using
# values from the debconf database.
#
# Edit this file with caution, and see the XF86Config-4 manual page.
# (Type "man XF86Config-4" at the shell prompt.)
#
# This file is automatically updated on xserver-xfree86 package upgrades *only*
# if it has not been modified since the last upgrade of the xserver-xfree86
# package.
#
# If you have edited this file but would like it to be automatically updated
# again, run the following commands as root:
#
#   cp /etc/X11/XF86Config-4 /etc/X11/XF86Config-4.custom
#   md5sum /etc/X11/XF86Config-4 >/var/lib/xfree86/XF86Config-4.md5sum
#   dpkg-reconfigure xserver-xfree86

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
	Load	"GLcore"
	Load	"bitmap"
	Load	"dbe"
	Load	"ddc"
	Load	"dri"
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
	Option		"XkbModel"	"pc104"
	Option		"XkbLayout"	"us"
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
	Identifier	"NVIDIA"
	Driver		"nvidia"
	BusID		"PCI:1:0:0"
        Option          "RenderAccel"           "true"
        Option          "NvAGP"                 "1"
        Option 		"AllowGLXWithComposite" "true"

EndSection

Section "Monitor"
	Identifier	"Viewsonic"
	HorizSync	30-86
	VertRefresh	50-180
	Option		"DPMS"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"NVIDIA"
	Monitor		"Viewsonic"
	DefaultDepth 	24
	Option          "TwinView"              "true"
	Option          "SecondMonitorHorizSync" "30-70"
        Option          "SecondMonitorVertRefresh" "50-120"
	Option          "MetaModes" "1152x864, 1152x864; 1152x864, 1152x864;"
	Option          "TwinViewOrientation" "RightOf"

	Subsection "Display"
		Depth 24
		Modes "1152x864"
		ViewPort 0 0 
	EndSubsection
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		"Default Screen"
	InputDevice	"Generic Keyboard"
	InputDevice	"Configured Mouse"
EndSection

#Section "DRI"
#	Mode	0666
#EndSection

Section "Extensions"
#	Option 	"Composite" "Enable"
	Option 	"Composite" "Disable"
EndSection

```[/QUOTE]
 It's now working here also. I think there was a temporary problem in the versioning of the kernel vs the versioning of the nvidia package getting out of synch. I forget where I got the reference for that from - someplace in bugzilla.

---

### Post by graabein on 2005-04-14
[QUOTE=tennessee@tennessee.id.au]It's now working here also. I think there was a temporary problem in the versioning of the kernel vs the versioning of the nvidia package getting out of synch. I forget where I got the reference for that from - someplace in bugzilla.[/QUOTE]
Any more info on this? I've got NVIDIA Gainward 6600GT 128MB and upgraded from Warty to Hoary when Hoary was released. Been having problems with OpenGL. X and screen resolution is okay but when I try glxinfo I get segmentation fault.

I've read up on quite a few problems, some saying that the Ubuntu drivers won't run on 6600GT and some saying that the new official driver (7174) is buggy and that the old 6629(?) is okay... Other sources say that "dri" and/or "glx" modules has to be disabled, "NvAGP" option has to be "1" or "2", and so on...

Anyway, I have a TV hooked up to the card (can't remember how - I'm at work now) that I want to play movies on. 

Does someone have a similar working system set up? I'd appreciate some help cause I'm quite the newbie, ie. what drivers to install, xorg.conf, what tests to run.

---

### Post by nad on 2005-04-15
The Xorg x server seems to have a problem initializing a second video card. This is independent of the nVidia driver as the closed source driver works fine with XFree. See your /var/log/Xorg.0.log (/var/log/Xorg.1.log for those of you trying to configure a second screen layout) and your ~/.xsession-errors log. Warty uses the XFree86 x server. I have not had a problem initializing separately addressable gpu's with the XFree server. Hoary depends on the Xorg server, so removing and installing the XFree server is _not_ an option.

I am continuing to test configurations and will continue to post.

Dan M

---

### Post by nad on 2005-04-15
Ummm... Posted last message to wrong thread.

Should have been: xorg.conf / multihead display problems

Apologies. Would a moderator please move it. Thanks.

Dan M

---

### Post by tim@bigredtree.com on 2005-05-25
After spending about 2 weeks reading forums and system/nvidia documentation
I was able to put together a smooth running Xorg.conf file. 

My computer is a:
AMD Barton 2500+ 
FIC AU13 mobo
Ubuntu (Hoary)
512Mb Ram
eVGA nVidia GeForce FX 5200
Basic 20" monitor
Zenith 21" TV

I was initially very confused because during those 2 weeks I had not really played with linux before. Luckily the console pointed me to the var/log/Xorg.0.log file. Through trial and error I was able to put this together. 
Step 1:
```

Download cpu specific drivers from http://www.nvidia.com/object/linux.html
Current driver for 32bit processor is 1.0-7174
!!!! Read README.txt @ ftp://download.nvidia.com/XFree86/Linux-x86/1.0-7174/README.txt
Install using instructions from README.txt entitled:
(sec-02) INSTALLING THE NVIDIA DRIVER

```
Step 2:
```

sudo gedit /etc/modules
add "nvidia" to the bottom of the list.

```
Step 3:
Edit your /etc/X11/xorg.conf file as follows(complete uncommented file included 
at bottom):
Go to Section "ServerLayout"
```

Section "ServerLayout"
#[REQUIRED]Identifies this layout
        Identifier  "two monitors"
#[REQUIRED]Defines which screen to load
        Screen  0 "Screen0"
#[REQUIRED]Don't change these if they work
        InputDevice "Mouse1" "CorePointer"
        InputDevice "Keyboard1" "CoreKeyboard"
EndSection

```
Go to Section "Module"
```

Section "Module"
        Load        "dbe"       # Double buffer extension
                SubSection  "extmod"
                        Option    "omit xfree86-dga"   # don't initialise the DGA extension
                EndSubSection
        Load        "type1"
        Load        "freetype"
#[REQUIRED-FOR-NVIDIA-DRIVER]loads the glx library
        Load        "glx"
#[REQUIRED-FOR-NVIDIA-DRIVER]delete or comment out using "#"
#     Load      "dri"
#[REQUIRED-FOR-NVIDIA-DRIVER]delete or comment out using "#"
#       Load    "GLcore"
EndSection

```
Go to Section "Monitor"
```

#[REQUIRED]This Section is required for first display, but second display will be #defined under the device section
Section "Monitor"
        Identifier  "CRT"
        HorizSync   30-50
        VertRefresh 59.94
EndSection

```
Go to Section "Device"
```

Section "Device"
#[REQUIRED]you can choose identifier, but remember, wherever the card is referenced
#this identifier is used
        Identifier  "NVIDIA GeForce"
#[REQUIRED]The correct name of driver installed in step 1 is "nvidia"
        Driver      "nvidia"
#[OPTIONAL]You can enter VideoRam if you want to, just make sure it is accurate
        VideoRam    131072
#[REQUIRED-FOR-TWINVIEW]Tells the boot utility what displays to configure
        Option  "ConnectedMonitor" "CRT,TV"
#[READ-README.txt](app-f)  APPENDIX F: CONFIGURING AGP
        Option "NvAGP" "3"
#[OPTIONAL]Disables Nvidia logo at startup
        Option "NoLogo" "true"
######[OPTIONAL/EXPERIMENTAL]Enable or disable hardware acceleration of ######the RENDER extension. ENABLE IT AT YOUR OWN RISK.
        Option "RenderAccel" "true"
#[OPTIONAL]Disable the RENDER extension.
        Option "NoRenderExtension" "false"
#[OPTIONAL]Asks card to query attached devices, will not work with most tv's
        Option "UseEdidFreqs" "no"
#[REQUIRED-FOR-Twinview] can be set to true/false or 1/0 or yes/no
        Option "TwinView" "1"
#[REQUIRED-FOR-Twinview]Define layout of displays:
# Takes one of the following  values: "RightOf" "LeftOf" "Above" "Below" "Clone".
        Option "TwinViewOrientation" "TV RightOf CRT"
#[REQUIRED-FOR-Twinview]Define settings for second display, I found these in
# the file /var/log/Xorg.0.log in the form below:
#(**) NVIDIA(0): Validated modes for display device TV-0:
#(**) NVIDIA(0):      Default mode "1024x768": 65.0 MHz, 48.4 kHz, 60.0 Hz
        Option      "SecondMonitorHorizSync" "48.4"
        Option      "SecondMonitorVertRefresh" "60"
#[REQUIRED-FOR-Twinview]resolution of displays in the form "display0,display1;..."
        Option      "MetaModes" "1600x1200,1600x1200;1280x1024,1280x1024;1024x768, 1024x768;1024x768,640x480;800x600,800x600;640x480,640x480;"
#                                               TV-OUT options !
#[REQUIRED-IF-DIFFERENT-FROM-THESE]Defined in:
# (app-j)  APPENDIX J: CONFIGURING TV-OUT
        Option "TVStandard" "NTSC-M" #nVidia driver default USA standard
        Option "TVOutFormat" "SVIDEO" #SVIDEO is the default
EndSection

```
Go to Section "Screen"
```

#[REQUIRED]This section is only needed to define the first display...
#The second display will be defined by X system if your device section is correct
Section "Screen"
    Identifier  "Screen0"
    Device      "NVIDIA GeForce"
    Monitor     "CRT"
    DefaultDepth 24

    Subsection "Display"
        Depth       8
        Modes      "3200x1200" "2560x1024" "1024x768" "1600x600" "1280x480"
        ViewPort    0 0
    EndSubsection
    Subsection "Display"
        Depth       16
        Modes      "3200x1200" "2560x1024" "1024x768" "1600x600" "1280x480"
        ViewPort    0 0
    EndSubsection
    Subsection "Display"
        Depth       24
        Modes      "3200x1200" "2560x1024" "1024x768" "1600x600" "1280x480"
        ViewPort    0 0
    EndSubsection
EndSection

```
And finally, here is the whole thing as it is working on my machine:
```


# **********************************************************************
# Refer to the xorg.conf(5x) man page for details about the format of 
# this file.
# **********************************************************************

# **********************************************************************
# Module section -- this  section  is used to specify
# which dynamically loadable modules to load.
# **********************************************************************
#
Section "Module"

# This loads the DBE extension module.

    Load        "dbe"  	# Double buffer extension

# This loads the miscellaneous extensions module, and disables
# initialisation of the XFree86-DGA extension within that module.
    SubSection  "extmod"
      Option    "omit xfree86-dga"   # don't initialise the DGA extension
    EndSubSection

# This loads the font modules
	Load        "type1"
	Load        "freetype"
	Load	"int10
	Load       "glx"

EndSection

# **********************************************************************
# Files section.  This allows default font and rgb paths to be set
# **********************************************************************

Section "Files"

    RgbPath	"/usr/X11R6/lib/X11/rgb"

# Multiple FontPath entries are allowed (which are concatenated together),
# as well as specifying multiple comma-separated entries in one FontPath
# command (or a combination of both methods)
# 
# 

	FontPath   "/usr/X11R6/lib/X11/fonts/misc/"
	FontPath   "/usr/X11R6/lib/X11/fonts/Type1/"
	FontPath   "/usr/X11R6/lib/X11/fonts/75dpi/"
	FontPath   "/usr/X11R6/lib/X11/fonts/100dpi/"
	FontPath   "/usr/X11R6/lib/X11/fonts/TrueType/"

# The module search path.  The default path is shown here.

#    ModulePath "/usr/X11R6/lib/modules"

EndSection

# **********************************************************************
# Server flags section.
# **********************************************************************

Section "ServerFlags"

#    Option "DisableVidModeExtension"

# Uncomment this to enable the use of a non-local xvidtune client. 

#    Option "AllowNonLocalXvidtune"

# Uncomment this to disable dynamically modifying the input device
# (mouse and keyboard) settings. 

#    Option "DisableModInDev"

# Uncomment this to enable the use of a non-local client to
# change the keyboard or mouse settings (currently only xset).

#    Option "AllowNonLocalModInDev"

EndSection

# **********************************************************************
# Input devices
# **********************************************************************

# 	**********************************************************************
# 	Core keyboard's InputDevice section
# 	**********************************************************************

Section "InputDevice"

    Identifier	"Keyboard1"
    Driver	"kbd"
    Option "XkbRules"	"xorg"
    Option "XkbModel"	"pc104"
    Option "XkbLayout"	"us"

EndSection


# 	**********************************************************************
# 	Core Pointer's InputDevice section
# 	**********************************************************************

Section "InputDevice"
	Identifier	"Mouse1"
	Driver		"mouse"
	Option		"CorePointer"
	Option		"Device"		"/dev/input/mice"
	Option		"Protocol"		"ImPS/2"
	Option		"Emulate3Buttons"	"true"
	Option		"ZAxisMapping"		"4 5"
EndSection


# Emulate3Buttons is an option for 2-button Microsoft mice
# Emulate3Timeout is the timeout in milliseconds (default is 50ms)

#    Option "Emulate3Buttons"
#    Option "Emulate3Timeout"    "50"

# ChordMiddle is an option for some 3-button Logitech mice

#    Option "ChordMiddle"

# **********************************************************************
# Monitor section
# **********************************************************************

# Any number of monitor sections may be present
# HorizSync is in kHz unless units are specified.
# HorizSync may be a comma separated list of discrete values, or a
# comma separated list of ranges of values.
# VertRefresh is in Hz unless units are specified.
# VertRefresh may be a comma separated list of discrete values, or a
# comma separated list of ranges of values.
# NOTE: THE VALUES HERE ARE EXAMPLES ONLY.  REFER TO YOUR MONITOR'S
# USER MANUAL FOR THE CORRECT NUMBERS.

Section "Monitor"
	Identifier  "CRT"
	HorizSync   30-50
	VertRefresh 59.94
EndSection


# **********************************************************************
# Graphics device section
# **********************************************************************

Section "Device"

	Identifier  "NVIDIA GeForce"
	Driver      "nvidia"
	VideoRam    131072
	Option	"ConnectedMonitor" "CRT,TV"
	Option "NvAGP" "3"
	Option "NoLogo" "true"
	Option "RenderAccel" "true"
	Option "NoRenderExtension" "false"
	Option "UseEdidFreqs" "yes"
# 						TV-OUT options !
	Option "TwinView" "1"
	Option "TwinViewOrientation" "TV RightOf CRT"
	Option      "MetaModes" "1600x1200,1600x1200;1280x1024,1280x1024;1024x768, 1024x768;1024x768,640x480;800x600,800x600;640x480,640x480;"
	Option "TVStandard" "NTSC-M"
	Option "TVOutFormat" "CONVERSION"
#	Option "TVOverScan" "0.6"
        Option      "SecondMonitorHorizSync" "48.4"
        Option      "SecondMonitorVertRefresh" "60"


EndSection


# **********************************************************************
# Screen sections
# **********************************************************************

# Any number of screen sections may be present.  Each describes
# the configuration of a single screen.  A single specific screen section
# may be specified from the X server command line with the "-screen"
# option.
Section "Screen"
    Identifier  "Screen0"
    Device      "NVIDIA GeForce"
    Monitor     "CRT"
    DefaultDepth 24

    Subsection "Display"
        Depth       8
	Modes      "3200x1200" "2560x1024" "1024x768" "1600x600" "1280x480"
        ViewPort    0 0
    EndSubsection
    Subsection "Display"
        Depth       16
	Modes      "3200x1200" "2560x1024" "1024x768" "1600x600" "1280x480"
        ViewPort    0 0
    EndSubsection
    Subsection "Display"
        Depth       24
        Modes      "3200x1200" "2560x1024" "1024x768" "1600x600" "1280x480"
        ViewPort    0 0
    EndSubsection
EndSection


# **********************************************************************
# ServerLayout sections.
# **********************************************************************

# Any number of ServerLayout sections may be present.  Each describes
# the way multiple screens are organised.  A specific ServerLayout
# section may be specified from the X server command line with the
# "-layout" option.  In the absence of this, the first section is used.
# When now ServerLayout section is present, the first Screen section
# is used alone.

Section "ServerLayout"

# The Identifier line must be present
    Identifier  "two monitors"

# Each Screen line specifies a Screen section name, and optionally
# the relative position of other screens.  The four names after
# primary screen name are the screens to the top, bottom, left and right
# of the primary screen.  In this example, screen 2 is located to the
# right of screen 1.

	Screen  0 "Screen0"
	InputDevice "Mouse1" "CorePointer"
	InputDevice "Keyboard1" "CoreKeyboard"

EndSection

# Section "DRI"
#    Mode 0666
# EndSection

```

---

### Post by zenrox on 2005-05-25
hears ab exampole of xinerma
that does span bolth montiors
<quote>
# /etc/X11/xorg.conf (xorg X Window System server configuration file)
#
# This file was generated by dexconf, the Debian X Configuration tool, using
# values from the debconf database.
#
# Edit this file with caution, and see the /etc/X11/xorg.conf manual page.
# (Type "man /etc/X11/xorg.conf" at the shell prompt.)
#
# This file is automatically updated on xserver-xorg package upgrades *only*
# if it has not been modified since the last upgrade of the xserver-xorg
# package.
#
# If you have edited this file but would like it to be automatically updated
# again, run the following commands:
#
#   cp /etc/X11/xorg.conf /etc/X11/xorg.conf.custom
#   sudo sh -c 'md5sum /etc/X11/xorg.conf >/var/lib/xfree86/xorg.conf.md5sum'
#   sudo dpkg-reconfigure xserver-xorg

Section "Files"
	FontPath	"unix/:7100"			# local font server
	# if the local font server has problems, we can fall back on these
	FontPath	"/usr/lib/X11/fonts/misc"
	FontPath	"/usr/lib/X11/fonts/cyrillic"
	FontPath	"/usr/lib/X11/fonts/100dpi/:unscaled"
	FontPath	"/usr/lib/X11/fonts/75dpi/:unscaled"
	FontPath	"/usr/lib/X11/fonts/Type1"
	FontPath	"/usr/lib/X11/fonts/CID"
	FontPath	"/usr/lib/X11/fonts/100dpi"
	FontPath	"/usr/lib/X11/fonts/75dpi"
        # paths to defoma fonts
	FontPath	"/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
	FontPath	"/var/lib/defoma/x-ttcidfont-conf.d/dirs/CID"
EndSection

Section "Module"
	Load	"bitmap"
	Load	"dbe"
	Load	"ddc"
	Load	"extmod"
	Load	"freetype"
	Load	"glx"
	Load	"int10"
	Load	"record"
	Load	"type1"
	Load	"v4l"
	Load	"vbe"
EndSection

Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"keyboard"
	Option		"CoreKeyboard"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc104"
	Option		"XkbLayout"	"us"
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
	Identifier	"NVIDIA Corporation NV28 [GeForce4 Ti 4800 SE]1"
	Driver		"nvidia"
	BusID		"PCI:1:0:0"
	#Option "NODDC"      "1"
	Screen  0
	#VideoRam	131000
EndSection

Section "Device"
	Identifier	"NVIDIA Corporation NV28 [GeForce4 Ti 4800 SE]2"
	Driver		"nvidia"
	BusID		"PCI:1:0:0"
	#Option "NODDC"      "1"
	Screen 1 
	#VideoRam	131000
EndSection

Section "Monitor"
	Identifier	"Generic Monitor1"
	Option		"DPMS"
	HorizSync	30-98
	VertRefresh	50-160
EndSection

Section "Monitor"
	Identifier	"Generic Monitor2"
	Option		"DPMS"
	HorizSync	30-70
	VertRefresh	50-160
EndSection

Section "Screen"
	Identifier	"Default Screen1"
	Device		"NVIDIA Corporation NV28 [GeForce4 Ti 4800 SE]1"
	Monitor		"Generic Monitor1"
	DefaultDepth	24
	SubSection "Display"
		Depth		16
		Modes		"1600x1200" "1280x1024" "1024x768" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1600x1200" "1280x1024" "1024x768" "800x600" "720x400" "640x480"
	EndSubSection
EndSection

Section "Screen"
	Identifier	"Default Screen2"
	Device		"NVIDIA Corporation NV28 [GeForce4 Ti 4800 SE]2"
	Monitor		"Generic Monitor2"
	DefaultDepth	24
SubSection "Display"
		Depth		24
		Modes		"1280x1024" "1024x768" "800x600" "720x400" "640x480"
	EndSubSection
EndSection

Section "ServerFlags"
 Option "Xinerama" "True"
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
	Screen 0	"Default Screen1"
	Screen 1  	"Default Screen2" leftOf "Default Screen1"
	InputDevice	"Generic Keyboard"
	InputDevice	"Configured Mouse"
EndSection

Section "DRI"
	Mode	0666
EndSection
</quote>
not pritty but works on hoary
and an nvidia ti4800 dvi , vga

---

