---
title: "compaq presario R3000 Hoary xorg.conf"
date: 2005-03-14
forum: General Help
---

### Post by tryphon_bzh on 2005-03-14
Hello everybody, sorry to bother you with so specific settings:
It's only for a Compaq Presario R3000 laptop.
Warty install was a success, but when upgrading to Hoary, I had trouble with the configuration of Xorg... I finally fixed it, after a long long time, trying a lot of tricks. I would like to avoid those painfull momments to others, so here is my laptop configuration:
hardware:
GeForce4 440 Go 64M
AMD Athlon(tm) XP Processor 3000+
WXGA LCD monitor 1280x800
Hoary packages installed:
linux-restricted-modules-2.6.10-4-k7
xorg-driver-synaptics
xorg-common           6.8.2-2

lspci
0000:00:00.0 Host bridge: nVidia Corporation nForce3 Host Bridge (rev a4)
0000:00:01.0 ISA bridge: nVidia Corporation nForce3 LPC Bridge (rev a6)
0000:00:01.1 SMBus: nVidia Corporation nForce3 SMBus (rev a4)
0000:00:02.0 USB Controller: nVidia Corporation nForce3 USB 1.1 (rev a5)
0000:00:02.1 USB Controller: nVidia Corporation nForce3 USB 1.1 (rev a5)
0000:00:02.2 USB Controller: nVidia Corporation nForce3 USB 2.0 (rev a2)
0000:00:06.0 Multimedia audio controller: nVidia Corporation nForce3 Audio (rev a2)
0000:00:06.1 Modem: nVidia Corporation: Unknown device 00d9 (rev a2)
0000:00:08.0 IDE interface: nVidia Corporation nForce3 IDE (rev a5)
0000:00:0a.0 PCI bridge: nVidia Corporation nForce3 PCI Bridge (rev a2)
0000:00:0b.0 PCI bridge: nVidia Corporation nForce3 AGP Bridge (rev a4)
0000:00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 NorthBridge
0000:00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 NorthBridge
0000:00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 NorthBridge
0000:00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 NorthBridge
0000:01:00.0 VGA compatible controller: nVidia Corporation NV17 [GeForce4 440 Go 64M] (rev a3)
0000:02:00.0 FireWire (IEEE 1394): Texas Instruments TSB43AB21 IEEE-1394a-2000 Controller (PHY/Link)
0000:02:01.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
0000:02:02.0 Network controller: Broadcom Corporation BCM4306 802.11b/g Wireless LAN Controller (rev 03)
0000:02:04.0 CardBus bridge: Texas Instruments: Unknown device ac54 (rev 01)
0000:02:04.1 CardBus bridge: Texas Instruments: Unknown device ac54 (rev 01)
0000:02:04.2 System peripheral: Texas Instruments: Unknown device 8201 (rev 01)


And the xorg.conf file that works for me. Sorry it just don't know why it works, and why other xorg.conf files I've found on internet just don't... hoping this will be usefull for someone.
/etc/X11/xorg.conf:

# **********************************************************************
# Refer to the xorg.conf(5) man page for details about the format of
# this file.
# **********************************************************************

# **********************************************************************
# Module section -- this  section  is used to specify
# which dynamically loadable modules to load.
# **********************************************************************
#
Section "Module"
#	Load	"GLcore"
	Load	"synaptics"
	Load	"bitmap"
	Load	"dbe"
	Load	"ddc"
#	Load	"dri"
	Load	"extmod"
	Load	"freetype"
	Load	"glx"
	Load	"int10"
	Load	"record"
	Load	"speedo"
	Load	"type1"
	Load	"vbe"
EndSection


# **********************************************************************
# Files section.  This allows default font and rgb paths to be set
# **********************************************************************

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
EndSection

# **********************************************************************
# Server flags section.
# **********************************************************************

Section "ServerFlags"

# Uncomment this to cause a core dump at the spot where a signal is
# received.  This may leave the console in an unusable state, but may
# provide a better stack trace in the core dump to aid in debugging

#    Option "NoTrapSignals"

# Uncomment this to disable the <Crtl><Alt><Fn> VT switch sequence
# (where n is 1 through 12).  This allows clients to receive these key
# events.

#    Option "DontVTSwitch"

# Uncomment this to disable the <Crtl><Alt><BS> server abort sequence
# This allows clients to receive this key event.

#    Option "DontZap"

# Uncomment this to disable the <Crtl><Alt><KP_+>/<KP_-> mode switching
# sequences.  This allows clients to receive these key events.

#    Option "Dont Zoom"

# Uncomment this to disable tuning with the xvidtune client. With
# it the client can still run and fetch card and monitor attributes,
# but it will not be allowed to change them. If it tries it will
# receive a protocol error.

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

# **********************************************************************
# Core keyboard's InputDevice section
# **********************************************************************

Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"keyboard"
	Option		"CoreKeyboard"
	Option		"XkbRules"	"xfree86"
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"fr"
EndSection


# **********************************************************************
# Core Pointer's InputDevice section
# **********************************************************************

# These parameters obtained from a mailing list post somewhere...
Section "InputDevice"
	Identifier	"Alps Touchpad"
	Driver		"synaptics"
	Option		"CorePointer"
	Option		"Device"		"/dev/input/event1"
	Option		"Protocol"		"event"
	Option		"LeftEdge"		"60"
	Option		"RightEdge"		"830"
	Option		"TopEdge"		"70"
	Option		"BottomEdge"		"650"
	Option		"FingerLow"		"25"
	Option		"FingerHigh"		"30"
	Option		"MaxTapTime"		"180"
	Option		"MaxTapMove"		"110"
	Option		"EmulateMidButtonTime"	"75"
	Option		"VertScrollDelta"	"50"
	Option		"HorizScrollDelta"	"50"
	Option		"MinSpeed"		"0.2"
	Option		"MaxSpeed"		"0.5"
	Option		"AccelFactor"		"0.01"
	Option		"EdgeMotionSpeed"	"40"
	Option		"UpDownScrolling"	"1"
	Option		"TouchpadOff"	"0"
EndSection

Section "InputDevice"
	Identifier	"USB Mouse"
	Driver		"mouse"
	Option		"SendCoreEvents"	"true"
	Option		"Device"		"/dev/input/mice"
	Option		"Protocol"		"ImPS/2"
	Option		"Emulate3Buttons"	"true"
	Option		"ZAxisMapping"		"4 5"
EndSection

# **********************************************************************
# Monitor section
# **********************************************************************

Section "Monitor"
    Identifier "monitor1"
    VendorName "Generic"
    ModelName "Flat Panel 1280x800"
        HorizSync       28-64
        VertRefresh     43-60
        Option          "DPMS"

#    HorizSync 31.5-90
#    VertRefresh 60

#Modeline "1280x800 at 70" 101.92 1280 1312 1696 1728 800 816 825 841
	Modeline        "1280x800 at 60" 83.91 1280 1312 1624 1656 800 816 824 841


    
    # Sony Vaio C1(X,XS,VE,VN)?
    # 1024x480 @ 85.6 Hz, 48 kHz hsync
    #ModeLine "1024x480"    65.00 1024 1032 1176 1344   480  488  494  563
-hsync -vsync
    
    # Dell D800 and few Inspiron (16/10) 1280x800
    # default : no (driver refuse to load)
    #ModeLine "1280x800 at 60"  147.89  1280 1376 1512 1744  800 801 804 848
    # samsung : yes !
    #ModeLine "1280x800 at 60"  71.0  1280 1328 1360 1440  800 802 808 823
    # 60Hz : yes !
    #ModeLine "1280x800 at 60"  83.5  1280 1344 1480 1680  800 801 804 828
    # ?? : yes !
    #ModeLine "1280x800"  85.7  1280 1360 1496 1712  800 801 804 835
    # 70Hz : no (lesser ersolution + scrolling)
    #ModeLine "1280x800"  101.92  1280 1312 1696 1728  800 816 824 841
    
    
EndSection

# **********************************************************************
# Graphics device section
# **********************************************************************

# Any number of graphics device sections may be present


# Device configured by xorgconfig:

Section "Device"
    Identifier  "geforce"
    #Driver      "vesa"
    Driver      "nvidia"
    Option "DPMS"
    Option "IgnoreEDID" "1"

    #VideoRam    65536
    # Insert Clocks lines here if appropriate
EndSection


# **********************************************************************
# Screen sections
# **********************************************************************

# Any number of screen sections may be present.  Each describes
# the configuration of a single screen.  A single specific screen section
# may be specified from the X server command line with the "-screen"
# option.
Section "Screen"
    Identifier  "Screen 1"
    Device      "geforce"
	Monitor "monitor1"
    DefaultDepth 24

    Subsection "Display"
        Depth       8
        #Modes       "1680x1050" "1280x1024" "1024x768" "800x600" "640x480"
	Modes		"1280x800"
        ViewPort    0 0
    EndSubsection
    Subsection "Display"
        Depth       16
        #Modes       "1680x1050" "1280x1024" "1024x768" "800x600" "640x480"
	Modes		"1280x800"
        ViewPort    0 0
    EndSubsection
    Subsection "Display"
        Depth       24
        #Modes       "1680x1050" "1280x1024" "1024x768" "800x600" "640x480"
	Modes		"1280x800 at 60"
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
    Identifier  "Simple Layout"

# Each Screen line specifies a Screen section name, and optionally
# the relative position of other screens.  The four names after
# primary screen name are the screens to the top, bottom, left and right
# of the primary screen.  In this example, screen 2 is located to the
# right of screen 1.

    Screen "Screen 1"

	InputDevice	"Generic Keyboard"
	InputDevice	"Alps Touchpad"
	InputDevice	"USB Mouse"

EndSection


Section "DRI"
	Mode	0666
EndSection

---

### Post by katu on 2005-03-30
You are now officially my personal hero  =D>  
I also don't seem to understand why it works, and i've tried many different options.
Once again I'm very grateful.
Katu

---

### Post by biodiesel-bri on 2005-11-01
I had a similar problem in my machine (different resolution though)

I think all you need to do is make sure this line is in your xorg.conf in the appropriate section:
Option "IgnoreEDID" "1"

Here's my working xorg.conf from a Compaq ZD7000 series (the one with the 17" monitor):

[COLOR="Red"](note that I use an external mouse.  I hate the touchpad so I pulled the relevant sections to get rid of the synaptics touchpad)[/COLOR]

```

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
# again, run the following command:
#   sudo dpkg-reconfigure -phigh xserver-xorg

Section "Files"
        FontPath        "/usr/share/X11/fonts/misc"
        FontPath        "/usr/share/X11/fonts/cyrillic"
        FontPath        "/usr/share/X11/fonts/100dpi/:unscaled"
        FontPath        "/usr/share/X11/fonts/75dpi/:unscaled"
        FontPath        "/usr/share/X11/fonts/Type1"
        FontPath        "/usr/share/X11/fonts/CID"
        FontPath        "/usr/share/X11/fonts/100dpi"
        FontPath        "/usr/share/X11/fonts/75dpi"
        # paths to defoma fonts
        FontPath        "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
        FontPath        "/var/lib/defoma/x-ttcidfont-conf.d/dirs/CID"
EndSection

Section "Module"
        #Load   "GLcore"
        Load    "i2c"
        Load    "bitmap"
        Load    "ddc"
        #Load   "dri"
        Load    "extmod"
        Load    "freetype"
        Load    "glx"
        Load    "int10"
        Load    "type1"
        Load    "vbe"
EndSection

Section "InputDevice"
        Identifier      "Generic Keyboard"
        Driver          "kbd"
        Option          "CoreKeyboard"
        Option          "XkbRules"      "xorg"
        Option          "XkbModel"      "pc104"
        Option          "XkbLayout"     "us"
EndSection

Section "InputDevice"
        Identifier      "Configured Mouse"
        Driver          "mouse"
        Option          "CorePointer"
        Option          "Device"                "/dev/input/mice"
        Option          "Protocol"              "ImPS/2"
        Option          "Emulate3Buttons"       "true"
        Option          "ZAxisMapping"          "4 5"
EndSection

Section "Device"
        Identifier      "NVIDIA Corporation NV34M [GeForce FX Go 5200]"
        Driver          "nvidia"
        BusID           "PCI:1:0:0"
        Option          "RenderAccel"           "On"
        Option          "NoRenderExtension"     "On"
        Option          "Accel"                 "On"
        Option          "IgnoreDisplayDevices"  "TV"
        Option          "NoLogo"                "On"
        Option          "AllowGLXWithComposite" "Off"
        Option          "IgnoreEDID"            "1"
        Option          "DPMS"
EndSection

Section "Monitor"
        Identifier      "Generic Monitor"
        Option          "DPMS"
        HorizSync       28-72
        VertRefresh     43-60
EndSection

Section "Screen"
        Identifier      "Default Screen"
        Device          "NVIDIA Corporation NV34M [GeForce FX Go 5200]"
        Monitor         "Generic Monitor"
        DefaultDepth    24
        SubSection "Display"
                Depth           1
                Modes           "1440x900"
        EndSubSection
        SubSection "Display"
                Depth           4
                Modes           "1440x900"
        EndSubSection
        SubSection "Display"
                Depth           8
                Modes           "1440x900"
        EndSubSection
        SubSection "Display"
                Depth           15
                Modes           "1440x900"
        EndSubSection
        SubSection "Display"
                Depth           16
                Modes           "1440x900"
        EndSubSection
        SubSection "Display"
                Depth           24
                Modes           "1440x900"
        EndSubSection
EndSection

Section "ServerLayout"
        Identifier      "Default Layout"
        Screen          "Default Screen"
        InputDevice     "Generic Keyboard"
        InputDevice     "Configured Mouse"
EndSection

Section "DRI"
        Mode    0666
EndSection
```

---

