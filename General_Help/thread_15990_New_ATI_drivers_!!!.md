---
title: "New ATI drivers !!!"
date: 2005-02-18
forum: General Help
---

### Post by bobmitch on 2005-02-18
I am running Hoary/Xorg (2.6.10-3-k7 kernel) with an ATI 9800 pro.

Using the new drivers from ATI I am now successfully running a harware accelerated dual head (large desktop) ubuntu. :)

If anyone is having problems with ATI cards, I strongly suggest getting these drivers and trying them out.

I will try and answer any questions anybody has trying to get them going.

Cheers,
mitch

---

### Post by artimess on 2005-02-18
Could you please write a howto for newbies, please.

Thanks

---

### Post by songochain on 2005-02-18
Hi dude! I've installed xorg-fglrx-drivers and i get 1600fps in glxgears, i think that it's a  shit score because a i've amd64 3200+ mobile with a radeon 9700 mobile. So i want to install this drivers to get more fps. I've a kernel image(2.6.10-3-amd64-k8) and linux-source-2.6.10, how can i install this drivers??
I've hoary for amd64
Thanks!

---

### Post by bobmitch on 2005-02-18
Ok, here's a quick, rough, worked-for-me-may-work-for-you guide.  (Not exactly noob friendly, but should get most people through it...)


1.   Download official driver .rpm from the ATI website.
2.   Remove fglrx packages using synaptic.
3.   Shut down gnome.  [  From terminal:  sudo /etc/init.d/gdm stop  ]
4.   cd to where you downloaded the driver rpm file.  
5.   sudo alien fglrx_6_8_0-8.10.19-1.i386.rpm 
6.   sudo mv /lib/modules/YOURKERNELVERSIONHERE/kernel/drivers/video/fglrx.ko $HOME
7.   dpkg --force-overwrite fglrx_6_8_0-8.10.19-1.i386.deb
8.   cd /lib/modules/fglrx/build_mod
9.   sudo sh make.sh
10. cd /lib/modules/fglrx
11. sudo sh make_install.sh
12. modprobe fglrx
13. fglrxconfig

---

### Post by songochain on 2005-02-18
Well... i get a error doing sh make.sh ```
ATI module generator V 2.0
==========================
initializing...
kernel includes at /lib/modules/2.6.10.18022005/build/include not found or incomplete
file: /lib/modules/2.6.10.18022005/build/include/linux/version.h

```I've Linux ximian64 2.6.10.18022005 kernel compiled by me
Thanks

---

### Post by bobmitch on 2005-02-18
[QUOTE=songochain]Well... i get a error doing sh make.sh ```
ATI module generator V 2.0
==========================
initializing...
kernel includes at /lib/modules/2.6.10.18022005/build/include not found or incomplete
file: /lib/modules/2.6.10.18022005/build/include/linux/version.h

```I've Linux ximian64 2.6.10.18022005 kernel compiled by me
Thanks[/QUOTE]

That header file should exist, and should contain 3 hash defines.  Here is mine:

#define UTS_RELEASE "2.6.10-3-k7"
#define LINUX_VERSION_CODE 132618
#define KERNEL_VERSION(a,b,c) (((a) << 16) + ((b) << 8) + (c))

I`m surprised the header file doesn`t exist....

---

### Post by songochain on 2005-02-18
[QUOTE=bobmitch]That header file should exist, and should contain 3 hash defines.  Here is mine:

#define UTS_RELEASE "2.6.10-3-k7"
#define LINUX_VERSION_CODE 132618
#define KERNEL_VERSION(a,b,c) (((a) << 16) + ((b) << 8) + (c))

I`m surprised the header file doesn`t exist....[/QUOTE]
 Sorry, i dont understand nothing :S can u explain it a bit more?

---

### Post by pagefault on 2005-02-18
[QUOTE=bobmitch]I am running Hoary/Xorg (2.6.10-3-k7 kernel) with an ATI 9800 pro.

Using the new drivers from ATI I am now successfully running a harware accelerated dual head (large desktop) ubuntu. :)

If anyone is having problems with ATI cards, I strongly suggest getting these drivers and trying them out.

I will try and answer any questions anybody has trying to get them going.

Cheers,
mitch[/QUOTE]

Yeah they work pretty good execpt for the fact that XVideo support does not work on dual monitor setups as they said it would in the changelog. So much for watching movies in dual head mode.

---

### Post by bobmitch on 2005-02-18
[QUOTE=pagefault]Yeah they work pretty good execpt for the fact that XVideo support does not work on dual monitor setups as they said it would in the changelog. So much for watching movies in dual head mode.[/QUOTE]

At the moment I am just glad I have dual head working - the rest can wait. ;)

But yes, I am pretty keen to get dual monitor video working - should look great on 2x21'' setup. :D

---

### Post by bobmitch on 2005-02-18
[QUOTE=songochain]Sorry, i dont understand nothing :S can u explain it a bit more?[/QUOTE]

Sorry - I guess what I should have said is I don`t know why you don`t have that particular file.

In fact, I`m not sure how you got the kernel compiled without getting problems with that file being missing in the first place.

---

### Post by Chris Ferrell on 2005-02-18
I guess composite is still disabled though?  At least I was never able to get xcompmgr to work with the proprietary drivers and the xorg radeon drivers were too slow to be usable.

---

### Post by bobmitch on 2005-02-19
[QUOTE=Chris Ferrell]I guess composite is still disabled though?  At least I was never able to get xcompmgr to work with the proprietary drivers and the xorg radeon drivers were too slow to be usable.[/QUOTE]

Yeah slipping the composite extension into the xorg.conf still kills the fglrx.  Radeon works as you say, but is unbearably slow.

---

### Post by songochain on 2005-02-19
[QUOTE=bobmitch]Sorry - I guess what I should have said is I don`t know why you don`t have that particular file.

In fact, I`m not sure how you got the kernel compiled without getting problems with that file being missing in the first place.[/QUOTE]
 Dude i forgot i did make mrproper a few days ago! I've recompiled and now i've installed ati drivers :D Thanks!

---

### Post by bobmitch on 2005-02-19
[QUOTE=songochain]Dude i forgot i did make mrproper a few days ago! I've recompiled and now i've installed ati drivers :D Thanks![/QUOTE]

Glad to hear it! :D

Now all we have to do is wait for the next driver release.... :)

---

### Post by Deusiah on 2005-02-25
Thanks for the instructions Bob Mitch. I'm quite a newbie to Linux but no stranger to computers.

I have even got dual head mode working for once. 1024x768 & 640x480 :)

I have a question about dual head mode however, is it possible to drag windows from one display to another or perhaps use some command to shove them to the other display? Perhaps I chose the wrong mode? I had an option of four to choose from however I was unsure of what the difference between some were and dual head seemed to be the right choice.

Anyway it's good to have 3D acceleration and Dual Head so thanks ;)

---

### Post by bobmitch on 2005-02-25
[QUOTE=Deusiah]Thanks for the instructions Bob Mitch. I'm quite a newbie to Linux but no stranger to computers.

I have even got dual head mode working for once. 1024x768 & 640x480 :)

I have a question about dual head mode however, is it possible to drag windows from one display to another or perhaps use some command to shove them to the other display? Perhaps I chose the wrong mode? I had an option of four to choose from however I was unsure of what the difference between some were and dual head seemed to be the right choice.

Anyway it's good to have 3D acceleration and Dual Head so thanks ;)[/QUOTE]

Glad to help - just be sure and add a plus to my reputation icon... ;)

It looks like you chose the dual head (two driver) mode, where you have an xserver running on each monitor.

What you want is the 'large desktop' option, whereby x is run across both monitors as a single desktop and you can easily move windows / apps anywhere you like across both.

Backup your existing xorg.conf file and rerun the fglrxconfig with sudo, making sure to choose the large desktop mode and you should be a happy chappy.

Rgds,
mitch

---

### Post by Deusiah on 2005-02-26
Hmm, this "repuation" thing is new to me, I usually use phpBB forums and have never seen such a thing. Anyway I figured it out :P

You know I was afraid you might say I'd have to run fglrxconfig again lol. Means I have to edit my XF86Config-4 file all over again just after I set it up as I wanted.

I was hoping there was a value you could change to get the desired layout, ohh well.

Thanks again for your help ;)

---

### Post by Deusiah on 2005-02-26
Well I just tried the "Big Desktop" setting. That's not what I wanted :( I can't have seperate resolutions if I enable that mode. It didn't behave like I expected. All it did was split the enitre display across two windows. What I was after is hard to explain unless you have seen it in Windows. It's like dual mode except there is no second desktop on the other screen, just an extention of the desktop but without splitting it into and it allows you to drag windows from one to the other.

I guess that can't be done in Linux with an ATI card. Perhaps Nvidia cards allow you to do this?

I'll guess I'll just have to keep it on Dual mode.

---

### Post by bobmitch on 2005-02-26
[QUOTE=Deusiah]Well I just tried the "Big Desktop" setting. That's not what I wanted :( I can't have seperate resolutions if I enable that mode. It didn't behave like I expected. All it did was split the enitre display across two windows. What I was after is hard to explain unless you have seen it in Windows. It's like dual mode except there is no second desktop on the other screen, just an extention of the desktop but without splitting it into and it allows you to drag windows from one to the other.

I guess that can't be done in Linux with an ATI card. Perhaps Nvidia cards allow you to do this?

I'll guess I'll just have to keep it on Dual mode.[/QUOTE]

Yeah, it sounds like dual mode is best for you at the moment.  Until ATI release a dedicated, working control panel for their drivers in linux, esoteric configurations will remain out of the reach of us mere mortals. :)

---

### Post by Torrilin on 2005-02-27
When I get to the point of ```
dpkg --force-overwrite fglrx_6_8_0-8.10.19-1.i386.deb
``` I get an error, ```
dpkg: need an action option
``` followed by some suggested commands. I'm a bit stuck since I can't see what I should change to make it work from the man pages and --help option.

Kalli

---

### Post by allans on 2005-02-27
No problem. just run it with the -i option, so your line will look like this :

sudo dpkg -i --force-version fglrx.....deb

The -i lets dpkg know you want to install the drivers.

---

### Post by Torrilin on 2005-02-27
Got past that. Then came the really fun part :o.

I didn't have the kernel headers or kernel source. Had to get that and install it. Also I was missing a gcc package. I needed build-essential and linux-source-2.6.8.1. The source code was packaged as a tar.bz2, so once I installed the package, I had to 
```

cd /usr/src/
sudo tar xjvf linux-source-2.6.8.1.tar.bz2
sudo ln -s linux-source-2.6.8.1 linux
```

This unzips and untars the source files and makes a symlink to the source in /usr/src/linux, where the ATI driver expects to find the source. Next you configure things so that the ATI driver knows where the build enviroment is.

```
cp /boot/config-2.6.8.1-3-k7 .config
cd /usr/src/linux-source-2.6.8.1
sudo pico Makefile
```

Change the variable EXTRAVERSION to match your kernel. In my case I changed it from .1 to .1-3-k7. Save the changes and exit.

```
sudo make oldconfig
sudo make prepare
sudo ln -s /usr/src/linux /usr/src/linux/lib/modules/2.6.8.1-3-k7/build
```

This completes the build enviroment for the ATI driver. The documentation I found on this section was more than a little shaky. Frequently the instructions for symlinks were not set up right, so you'd get broken symlinks, or some other key detail would be omitted.

Once I made these changes, the instructions worked up until it was time to restart X. I rebooted and got a black screen that flashed a couple of times, and the system hung. By reverting to an i386 kernel, I got x working again as a stopgap. I still haven't figured out what exactly is wrong with the x configuration on my k7 kernel. Need to stop and eat tho.

Kalli

---

### Post by Deusiah on 2005-02-28
Torrilin it sound like your doing things the long way around. I simply downloaded GCC, and the Kernel headers/source via synaptic and everything worked fine (until I tried to upgrade the system and it couldn't over write a module and my initrd was deleted but that's another story lol).

You shouldn't have to mess about setting up symlinks.

With regards to X hanging I have a similar problem if I try to use the internal Agpgart.

---

### Post by bobmitch on 2005-02-28
[QUOTE=Deusiah]Torrilin it sound like your doing things the long way around. I simply downloaded GCC, and the Kernel headers/source via synaptic and everything worked fine (until I tried to upgrade the system and it couldn't over write a module and my initrd was deleted but that's another story lol).

You shouldn't have to mess about setting up symlinks.

With regards to X hanging I have a similar problem if I try to use the internal Agpgart.[/QUOTE]

The internal AGPgart bug is a 'known' problem.  (One of many... ;)  )

---

### Post by Deusiah on 2005-03-01
That's nice to hear, I thought it was just my machine playing up lol.

---

### Post by songochain on 2005-03-01
I've problems since i did dist-upgrade today because now i've a new version of xorg that has problems with ati oficial drivers. ```
ACPI: PCI interrupt 0000:01:00.0[A] -> GSI 17 (level, low) -> IRQ 17
Trying to register duplicated ioctl32 handler c0246400
[fglrx:firegl_init_32compat_ioctls] *ERROR* unable to register ioctl32 0
[fglrx:firegl_init] *ERROR* Couldn't register compat32 ioctls!

``` Any idea??

---

### Post by delltony on 2005-03-01
[QUOTE=songochain]I've problems since i did dist-upgrade today because now i've a new version of xorg that has problems with ati oficial drivers. ```
ACPI: PCI interrupt 0000:01:00.0[A] -> GSI 17 (level, low) -> IRQ 17
Trying to register duplicated ioctl32 handler c0246400
[fglrx:firegl_init_32compat_ioctls] *ERROR* unable to register ioctl32 0
[fglrx:firegl_init] *ERROR* Couldn't register compat32 ioctls!

``` Any idea??[/QUOTE]
 I can not figure this out for the life of me. after following these steps for my ati radeon 9700 for my dell inspiron 9100 laptop I can't now use screen resolution.
When i go to system->preferences->screen resolution i get the following error.
[img]http://www.imageark.net/image.php?id=96064[/img]

here is a copy of my xorg.conf file
```

# File: xorg.conf
# File generated by fglrxconfig (C) ATI Research, a substitute for xf86config.

# Note by ATI: the below copyright notice is there for servicing possibly
# pending third party rights on the file format and the instance of this file.
#
# Copyright (c) 1999 by The XFree86 Project, Inc.
#
# Permission is hereby granted, free of charge, to any person obtaining a
# copy of this software and associated documentation files (the "Software"),
# to deal in the Software without restriction, including without limitation
# the rights to use, copy, modify, merge, publish, distribute, sublicense,
# and/or sell copies of the Software, and to permit persons to whom the
# Software is furnished to do so, subject to the following conditions:
# 
# The above copyright notice and this permission notice shall be included in
# all copies or substantial portions of the Software.
# 
# THE SOFTWARE IS PROVIDED "AS IS", WITHOUT WARRANTY OF ANY KIND, EXPRESS OR
# IMPLIED, INCLUDING BUT NOT LIMITED TO THE WARRANTIES OF MERCHANTABILITY,
# FITNESS FOR A PARTICULAR PURPOSE AND NONINFRINGEMENT.  IN NO EVENT SHALL
# THE XFREE86 PROJECT BE LIABLE FOR ANY CLAIM, DAMAGES OR OTHER LIABILITY,
# WHETHER IN AN ACTION OF CONTRACT, TORT OR OTHERWISE, ARISING FROM, OUT OF
# OR IN CONNECTION WITH THE SOFTWARE OR THE USE OR OTHER DEALINGS IN THE
# SOFTWARE.
# 
# Except as contained in this notice, the name of the XFree86 Project shall
# not be used in advertising or otherwise to promote the sale, use or other
# dealings in this Software without prior written authorization from the
# XFree86 Project.
#

# **********************************************************************
# Refer to the XF86Config(4/5) man page for details about the format of 
# this file.
# **********************************************************************

# **********************************************************************
# DRI Section
# **********************************************************************
Section "dri"
# Access to OpenGL ICD is allowed for all users:
    Mode 0666
# Access to OpenGL ICD is restricted to a specific user group:
#    Group 100    # users
#    Mode 0660
EndSection

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
#      Option    "omit xfree86-dga" 
    EndSubSection

# This loads the Type1 and FreeType font modules
    Load        "type1"
    Load        "freetype"

# This loads the GLX module
    Load        "glx"   # libglx.a
    Load        "dri"   # libdri.a

EndSection

# **********************************************************************
# Files section.  This allows default font and rgb paths to be set
# **********************************************************************

Section "Files"

# The location of the RGB database.  Note, this is the name of the
# file minus the extension (like ".txt" or ".db").  There is normally
# no need to change the default.

    RgbPath	"/usr/X11R6/lib/X11/rgb"

# Multiple FontPath entries are allowed (which are concatenated together),
# as well as specifying multiple comma-separated entries in one FontPath
# command (or a combination of both methods)
# 
# If you don't have a floating point coprocessor and emacs, Mosaic or other
# programs take long to start up, try moving the Type1 and Speedo directory
# to the end of this list (or comment them out).
# 

#    FontPath   "/usr/X11R6/lib/X11/fonts/local/"
    FontPath   "/usr/X11R6/lib/X11/fonts/misc/"
    FontPath   "/usr/X11R6/lib/X11/fonts/75dpi/:unscaled"
    FontPath   "/usr/X11R6/lib/X11/fonts/100dpi/:unscaled"
    FontPath   "/usr/X11R6/lib/X11/fonts/Type1/"
#    FontPath   "/usr/X11R6/lib/X11/fonts/Speedo/"
    FontPath   "/usr/X11R6/lib/X11/fonts/75dpi/"
    FontPath   "/usr/X11R6/lib/X11/fonts/100dpi/"

# The module search path.  The default path is shown here.

#    ModulePath "/usr/X11R6/lib/modules"

EndSection

# **********************************************************************
# Server flags section.
# **********************************************************************

Section "ServerFlags"

# Uncomment this to cause a core dump at the spot where a signal is 
# received.  This may leave the console in an unusable state, but may
# provide a better stack trace in the core dump to aid in debugging

#    Option "NoTrapSignals"

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

    Identifier	"Keyboard1"
    Driver	"kbd"
# For most OSs the protocol can be omitted (it defaults to "Standard").
# When using XQUEUE (only for SVR3 and SVR4, but not Solaris),
# uncomment the following line.

#    Option "Protocol"   "Xqueue"

    Option "AutoRepeat" "500 30"

# Specify which keyboard LEDs can be user-controlled (eg, with xset(1))
#    Option "Xleds"      "1 2 3"

#    Option "LeftAlt"    "Meta"
#    Option "RightAlt"   "ModeShift"

# To customise the XKB settings to suit your keyboard, modify the
# lines below (which are the defaults).  For example, for a non-U.S.
# keyboard, you will probably want to use:
#    Option "XkbModel"   "pc102"
# If you have a US Microsoft Natural keyboard, you can use:
#    Option "XkbModel"   "microsoft"
#
# Then to change the language, change the Layout setting.
# For example, a german layout can be obtained with:
#    Option "XkbLayout"  "de"
# or:
#    Option "XkbLayout"  "de"
#    Option "XkbVariant" "nodeadkeys"
#
# If you'd like to switch the positions of your capslock and
# control keys, use:
#    Option "XkbOptions" "ctrl:swapcaps"

# These are the default XKB settings for XFree86
#    Option "XkbRules"   "xfree86"
#    Option "XkbModel"   "pc101"
#    Option "XkbLayout"  "us"
#    Option "XkbVariant" ""
#    Option "XkbOptions" ""

#    Option "XkbDisable"

    Option "XkbRules"	"xfree86"
    Option "XkbModel"	"pc104"
    Option "XkbLayout"	"us"

EndSection


# **********************************************************************
# Core Pointer's InputDevice section
# **********************************************************************

Section "InputDevice"

# Identifier and driver

    Identifier	"Mouse1"
    Driver "mouse"
    Option "Protocol"   "PS/2"
    Option "Device"     "/dev/input/mice"

# When using XQUEUE, comment out the above two lines, and uncomment
# the following line.

#    Option "Protocol"   "Xqueue"

# Baudrate and SampleRate are only for some Logitech mice. In
# almost every case these lines should be omitted.

#    Option "BaudRate"   "9600"
#    Option "SampleRate" "150"

# Emulate3Buttons is an option for 2-button Microsoft mice
# Emulate3Timeout is the timeout in milliseconds (default is 50ms)

    Option "Emulate3Buttons"
#    Option "Emulate3Timeout"    "50"

# ChordMiddle is an option for some 3-button Logitech mice

#    Option "ChordMiddle"

EndSection


# **********************************************************************
# Other input device sections 
# this is optional and is required only if you
# are using extended input devices.  This is for example only.  Refer
# to the XF86Config man page for a description of the options.
# **********************************************************************
#
# Section "InputDevice" 
#    Identifier  "Mouse2"
#    Driver      "mouse"
#    Option      "Protocol"      "MouseMan"
#    Option      "Device"        "/dev/mouse2"
# EndSection
#
# Section "InputDevice"
#    Identifier "spaceball"
#    Driver     "magellan"
#    Option     "Device"         "/dev/cua0"
# EndSection
#
# Section "InputDevice"
#    Identifier "spaceball2"
#    Driver     "spaceorb"
#    Option     "Device"         "/dev/cua0"
# EndSection
#
# Section "InputDevice"
#    Identifier "touchscreen0"
#    Driver     "microtouch"
#    Option     "Device"         "/dev/ttyS0"
#    Option     "MinX"           "1412"
#    Option     "MaxX"           "15184"
#    Option     "MinY"           "15372"
#    Option     "MaxY"           "1230"
#    Option     "ScreenNumber"   "0"
#    Option     "ReportingMode"  "Scaled"
#    Option     "ButtonNumber"   "1"
#    Option     "SendCoreEvents"
# EndSection
#
# Section "InputDevice"
#    Identifier "touchscreen1"
#    Driver     "elo2300"
#    Option     "Device"         "/dev/ttyS0"
#    Option     "MinX"           "231"
#    Option     "MaxX"           "3868"
#    Option     "MinY"           "3858"
#    Option     "MaxY"           "272"
#    Option     "ScreenNumber"   "0"
#    Option     "ReportingMode"  "Scaled"
#    Option     "ButtonThreshold"    "17"
#    Option     "ButtonNumber"   "1"
#    Option     "SendCoreEvents"
# EndSection

# **********************************************************************
# Monitor section
# **********************************************************************

# Any number of monitor sections may be present

Section "Monitor"
    Identifier  "Monitor0"
    HorizSync   31.5-110
    VertRefresh 28-90
    Option "DPMS"

# === mode lines based on GTF ===
# VGA @ 100Hz
# Modeline "640x480@100" 43.163 640 680 744 848 480 481 484 509 +hsync +vsync
# SVGA @ 100Hz
# Modeline "800x600@100" 68.179 800 848 936 1072 600 601 604 636 +hsync +vsync
# XVGA @ 100Hz
# Modeline "1024x768@100" 113.309 1024 1096 1208 1392 768 769 772 814 +hsync +vsync
# 1152x864 @ 60Hz
# Modeline "1152x864@60" 81.642 1152 1216 1336 1520 864 865 868 895 +hsync +vsync
# 1152x864 @ 85Hz
# Modeline "1152x864@85" 119.651 1152 1224 1352 1552 864 865 868 907 +hsync +vsync
# 1152x864 @ 100Hz
# Modeline "1152x864@100" 143.472 1152 1232 1360 1568 864 865 868 915 +hsync +vsync
# 1280x960 @ 75Hz
# Modeline "1280x960@75" 129.859 1280 1368 1504 1728 960 961 964 1002 +hsync +vsync
# 1280x960 @ 100Hz
# Modeline "1280x960@100" 178.992 1280 1376 1520 1760 960 961 964 1017  +hsync +vsync
# SXGA @ 100Hz
# Modeline "1280x1024@100" 190.960 1280 1376 1520 1760 1024 1025 1028 1085 +hsync +vsync
# SPEA GDM-1950 (60Hz,64kHz,110MHz,-,-): 1280x1024 @ V-freq: 60.00 Hz, H-freq: 63.73 KHz
# Modeline "GDM-1950"  109.62  1280 1336 1472 1720  1024 1024 1026 1062 -hsync -vsync
# 1600x1000 @ 60Hz
# Modeline "1600x1000" 133.142 1600 1704 1872 2144 1000 1001 1004 1035 +hsync +vsync
# 1600x1000 @ 75Hz
# Modeline "1600x1000" 169.128 1600 1704 1880 2160 1000 1001 1004 1044 +hsync +vsync
# 1600x1000 @ 85Hz
# Modeline "1600x1000" 194.202 1600 1712 1888 2176 1000 1001 1004 1050 +hsync +vsync
# 1600x1000 @ 100Hz
# Modeline "1600x1000" 232.133 1600 1720 1896 2192 1000 1001 1004 1059 +hsync +vsync
# 1600x1024 @ 60Hz
# Modeline "1600x1024" 136.385 1600 1704 1872 2144 1024 1027 1030 1060 +hsync +vsync
# 1600x1024 @ 75Hz
# Modeline "1600x1024" 174.416 1600 1712 1888 2176 1024 1025 1028 1069 +hsync +vsync
# 1600x1024 @ 76Hz
# Modeline "1600x1024" 170.450 1600 1632 1792 2096 1024 1027 1030 1070 +hsync +vsync
# 1600x1024 @ 85Hz
# Modeline "1600x1024" 198.832 1600 1712 1888 2176 1024 1027 1030 1075 +hsync +vsync
# 1920x1080 @ 60Hz
# Modeline "1920x1080" 172.798 1920 2040 2248 2576 1080 1081 1084 1118 -hsync -vsync
# 1920x1080 @ 75Hz
# Modeline "1920x1080" 211.436 1920 2056 2264 2608 1080 1081 1084 1126 +hsync +vsync
# 1920x1200 @ 60Hz
# Modeline "1920x1200" 193.156 1920 2048 2256 2592 1200 1201 1203 1242 +hsync +vsync
# 1920x1200 @ 75Hz
# Modeline "1920x1200" 246.590 1920 2064 2272 2624 1200 1201 1203 1253 +hsync +vsync
# 2048x1536 @ 60
# Modeline "2048x1536" 266.952 2048 2200 2424 2800 1536 1537 1540 1589 +hsync +vsync
# 2048x1536 @ 60
# Modeline "2048x1536" 266.952 2048 2200 2424 2800 1536 1537 1540 1589 +hsync +vsync
# 1400x1050 @ 60Hz M9 Laptop mode 
# ModeLine "1400x1050" 122.000 1400 1488 1640 1880 1050 1052 1064 1082 +hsync +vsync
# 1920x2400 @ 25Hz for IBM T221, VS VP2290 and compatible display devices
# Modeline "1920x2400@25" 124.620 1920 1928 1980 2048 2400 2401 2403 2434 +hsync +vsync
# 1920x2400 @ 30Hz for IBM T221, VS VP2290 and compatible display devices
# Modeline "1920x2400@30" 149.250 1920 1928 1982 2044 2400 2402 2404 2434 +hsync +vsync

EndSection


# **********************************************************************
# Graphics device section
# **********************************************************************

# Any number of graphics device sections may be present

# Standard VGA Device:

Section "Device"
    Identifier  "Standard VGA"
    VendorName  "Unknown"
    BoardName   "Unknown"

# The chipset line is optional in most cases.  It can be used to override
# the driver's chipset detection, and should not normally be specified.

#    Chipset     "generic"

# The Driver line must be present.  When using run-time loadable driver
# modules, this line instructs the server to load the specified driver
# module.  Even when not using loadable driver modules, this line
# indicates which driver should interpret the information in this section.

    Driver      "vga"
# The BusID line is used to specify which of possibly multiple devices
# this section is intended for.  When this line isn't present, a device
# section can only match up with the primary video device.  For PCI
# devices a line like the following could be used.  This line should not
# normally be included unless there is more than one video device
# installed.

#    BusID       "PCI:0:10:0"

#    VideoRam    256

#    Clocks      25.2 28.3

EndSection

# === ATI device section ===

Section "Device"
    Identifier                          "ATI Graphics Adapter"
    Driver                              "fglrx"
# ### generic DRI settings ###
# === disable PnP Monitor  ===
    #Option                              "NoDDC"
# === disable/enable XAA/DRI ===
    Option "no_accel"                   "no"
    Option "no_dri"                     "no"
# === misc DRI settings ===
    Option "mtrr"                       "off" # disable DRI mtrr mapper, driver has its own code for mtrr
# ### FireGL DDX driver module specific settings ###
# === Screen Management ===
    Option "DesktopSetup"               "0x00000000" 
    Option "MonitorLayout"              "AUTO, AUTO"
    Option "IgnoreEDID"                 "off"
    Option "HSync2"                     "unspecified" 
    Option "VRefresh2"                  "unspecified" 
    Option "ScreenOverlap"              "0" 
# === TV-out Management ===
    Option "NoTV"                       "no"     
    Option "TVStandard"                 "NTSC-M"     
    Option "TVHSizeAdj"                 "0"     
    Option "TVVSizeAdj"                 "0"     
    Option "TVHPosAdj"                  "0"     
    Option "TVVPosAdj"                  "0"     
    Option "TVHStartAdj"                "0"     
    Option "TVColorAdj"                 "0"     
    Option "GammaCorrectionI"           "0x00000000"
    Option "GammaCorrectionII"          "0x00000000"
# === OpenGL specific profiles/settings ===
    Option "Capabilities"               "0x00000800"
# === Video Overlay for the Xv extension ===
    Option "VideoOverlay"               "on"
# === OpenGL Overlay ===
# Note: When OpenGL Overlay is enabled, Video Overlay
#       will be disabled automatically
    Option "OpenGLOverlay"              "off"
# === Center Mode (Laptops only) ===
    Option "CenterMode"                 "off"
# === Pseudo Color Visuals (8-bit visuals) ===
    Option "PseudoColorVisuals"         "off"
# === QBS Management ===
    Option "Stereo"                     "off"
    Option "StereoSyncEnable"           "1"
# === FSAA Management ===
    Option "FSAAEnable"                 "no"
    Option "FSAAScale"                  "1"
    Option "FSAADisableGamma"           "no"
    Option "FSAACustomizeMSPos"         "no"
    Option "FSAAMSPosX0"                "0.000000"
    Option "FSAAMSPosY0"                "0.000000"
    Option "FSAAMSPosX1"                "0.000000"
    Option "FSAAMSPosY1"                "0.000000"
    Option "FSAAMSPosX2"                "0.000000"
    Option "FSAAMSPosY2"                "0.000000"
    Option "FSAAMSPosX3"                "0.000000"
    Option "FSAAMSPosY3"                "0.000000"
    Option "FSAAMSPosX4"                "0.000000"
    Option "FSAAMSPosY4"                "0.000000"
    Option "FSAAMSPosX5"                "0.000000"
    Option "FSAAMSPosY5"                "0.000000"
# === Misc Options ===
    Option "UseFastTLS"                 "0"
    Option "BlockSignalsOnLock"         "on"
    Option "UseInternalAGPGART"         "yes"
    Option "ForceGenericCPU"            "no"
    BusID "PCI:1:0:0"    # vendor=1002, device=4e50
    Screen 0
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
    Device      "ATI Graphics Adapter"
    Monitor     "Monitor0"
    DefaultDepth 24
    #Option "backingstore"

    Subsection "Display"
        Depth       24
        Modes       "1280x1024" "1024x768" "800x600" "640x480"
        ViewPort    0 0  # initial origin if mode is smaller than desktop
#        Virtual     1280 1024
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
    Identifier  "Server Layout"

# Each Screen line specifies a Screen section name, and optionally
# the relative position of other screens.  The four names after
# primary screen name are the screens to the top, bottom, left and right
# of the primary screen.

    Screen "Screen0"

# Each InputDevice line specifies an InputDevice section name and
# optionally some options to specify the way the device is to be
# used.  Those options include "CorePointer", "CoreKeyboard" and
# "SendCoreEvents".

    InputDevice "Mouse1" "CorePointer"
    InputDevice "Keyboard1" "CoreKeyboard"

EndSection

### EOF ###

```

thanks for your help.

---

### Post by Jet2k5 on 2005-03-01
Just wanted to make a note to those of you guys who have the mobile cards.

I just roughly read through some of the posts, and didn't see anything that big on mobility cards.

As of right now these ATI Drivers DO NOT SUPPORT any mobile video card, expect from the M9 and up.  So the M6 ( which I have ) M7 and M8 are not supported, and don't try to get them to work, they will just hose your system!

I know it sucks, trust me I know!  I've wanted to get them to work, but I guess they are just old and no longer supported.

Anyways, good luck to you other guys who can enjoy having their cards working with Linux.  =D>

---

### Post by jsgotangco on 2005-03-01
I have M9 (Mobility Radeon 9000) but this config thing is so alien to me at the moment.

---

### Post by songochain on 2005-03-02
[QUOTE=Jet2k5]Just wanted to make a note to those of you guys who have the mobile cards.

I just roughly read through some of the posts, and didn't see anything that big on mobility cards.

As of right now these ATI Drivers DO NOT SUPPORT any mobile video card, expect from the M9 and up.  So the M6 ( which I have ) M7 and M8 are not supported, and don't try to get them to work, they will just hose your system!

I know it sucks, trust me I know!  I've wanted to get them to work, but I guess they are just old and no longer supported.

Anyways, good luck to you other guys who can enjoy having their cards working with Linux.  =D>[/QUOTE]
 Dude, now i've installed ati oficial drivers. The problem was that my compiled kernel was a big shit! I deleted modules that they're important. Now i use a linux-image and my ati runs correctly. I will probe a compiled kernel with more modules hehe

---

### Post by Jet2k5 on 2005-03-02
[QUOTE=songochain]Dude, now i've installed ati oficial drivers. The problem was that my compiled kernel was a big shit! I deleted modules that they're important. Now i use a linux-image and my ati runs correctly. I will probe a compiled kernel with more modules hehe[/QUOTE]
 What video card do you have?

---

### Post by UbuWu on 2005-03-02
Isn't there any easier way to install these drivers???  #-o

---

### Post by bobmitch on 2005-03-02
[QUOTE=UbuWu]Isn't there any easier way to install these drivers???  #-o[/QUOTE]

I do believe there exist debian packages somewhere on one of the internets - but I would rather wait for a backported ubuntu specific package.

Short answer: yes.  
Slightly longer answer: Yes, but I don`t know where they are off the top of my head and I wouldn`t trust too much unless someone else reports back here with their positive feedback on them.

---

### Post by songochain on 2005-03-02
I've a radeon mobility 9700. Now i've running a compiled kernel and ati oficial drivers too :D
Now i'm updating and ubuntu will install a new version of xorg, i'm scared because last update of xorg left a problem of dependencies (libglmesa or something)  [-(

---

### Post by delltony on 2005-03-03
[QUOTE=songochain]I've a radeon mobility 9700. Now i've running a compiled kernel and ati oficial drivers too :D
Now i'm updating and ubuntu will install a new version of xorg, i'm scared because last update of xorg left a problem of dependencies (libglmesa or something)  [-([/QUOTE]

that happened with me as well here is what I done.
I took and removed the ati offical driver and then did the updates
then put the driver back in.
without the ati driver open gl doesn't work correctly and the one from x.org also makes a xf86config-4 file instead of a xorg.conf file like it should. 
In any case try that method.

---

### Post by songochain on 2005-03-03
Done :D

---

### Post by PeP on 2005-03-04
I had some difficulties to install fglrx when I switched to kernel 2.6.11

I use Xfree, 
I downloaded the latest driver from ati for Xfree

then 
sudo alien fglrx_4_3_0-8.10.19-1.i386.rpm
dpkg -i fglrx... .deb
cd /lib/modules/fglrx/build.sh
sudo make.sh
-->> and it did not compile
I found many patches on the net for teh previous version (none worked for me)
so I edited the faulty file: I attached the patch

so I then did cd /lib/modules/fglrxI had some difficulties to install fglrx when I switched to kernel 2.6.11

I use Xfree, 
I downloaded the latest driver from ati for Xfree

then 
sudo alien fglrx_4_3_0-8.10.19-1.i386.rpm
dpkg -i fglrx... .deb
cd /lib/modules/fglrx/build.sh
sudo make.sh
-->> and it did not compile
sudo chmod -R u+w *
sudo patch -p0 < patch-fglrx-8.10.19.-1-kernel.2.6.11.txt
sudo make.sh
and it then worked


I hope it will be helpfull for someone.



And then the little bonus, with this new kernel and this new fglrx driver, glxgears runs twice as fast than the one from linux-restricted-modules on kernel-image-2.6.8.1-5

---

### Post by PeP on 2005-03-04
Did someone managed to make xinerama work with fglrx and dual display?

i have some difficulties:
- with xinerama one of the screen has an unreadable image
- with or without it (dual screen with 2 drivers) I cannnot launch X on my laptop when the external screen is not plugged
- with dual display,  switching on and of th screen with Fn-F7 does not work anymore
 
thanks

---

### Post by songochain on 2005-03-05
[QUOTE=PeP]I had some difficulties to install fglrx when I switched to kernel 2.6.11

I use Xfree, 
I downloaded the latest driver from ati for Xfree

then 
sudo alien fglrx_4_3_0-8.10.19-1.i386.rpm
dpkg -i fglrx... .deb
cd /lib/modules/fglrx/build.sh
sudo make.sh
-->> and it did not compile
I found many patches on the net for teh previous version (none worked for me)
so I edited the faulty file: I attached the patch

so I then did cd /lib/modules/fglrxI had some difficulties to install fglrx when I switched to kernel 2.6.11

I use Xfree, 
I downloaded the latest driver from ati for Xfree

then 
sudo alien fglrx_4_3_0-8.10.19-1.i386.rpm
dpkg -i fglrx... .deb
cd /lib/modules/fglrx/build.sh
sudo make.sh
-->> and it did not compile
sudo chmod -R u+w *
sudo patch -p0 < patch-fglrx-8.10.19.-1-kernel.2.6.11.txt
sudo make.sh
and it then worked


I hope it will be helpfull for someone.



And then the little bonus, with this new kernel and this new fglrx driver, glxgears runs twice as fast than the one from linux-restricted-modules on kernel-image-2.6.8.1-5[/QUOTE]
Dont work for me
```
songochain@ximian64:/lib/modules/fglrx/build_mod$ sudo patch -p0 < patch-fglrx-8 .10.19.-1-kernel.2.6.11.txt
can't find file to patch at input line 3
Perhaps you used the wrong -p or --strip option?
The text leading up to this was:
--------------------------
|--- build_mod/firegl_public.c  2005-02-10 03:15:05.000000000 +0100
|+++ build_mod2/firegl_public.c 2005-03-04 14:30:15.000000000 +0100
--------------------------
File to patch: firegl_public.c
patching file firegl_public.c
Reversed (or previously applied) patch detected!  Assume -R? [n] y
songochain@ximian64:/lib/modules/fglrx/build_mod$ sudo sh make.sh
make.sh: line 52: [: 3: unary operator expected
ATI module generator V 2.0
==========================
initializing...
cleaning...
patching 'highmem.h'...
assuming new VMA API since we do have kernel 2.6.x...
doing Makefile based build for kernel 2.6.x and higher
make -C /lib/modules/2.6.11.050305-songopowah/build SUBDIRS=/lib/modules/fglrx/b uild_mod/2.6.x modules
make[1]: Entering directory `/usr/src/linux-2.6.11'
  CC [M]  /lib/modules/fglrx/build_mod/2.6.x/firegl_public.o
/lib/modules/fglrx/build_mod/2.6.x/firegl_public.c: En la función `firegl_stub_p utminor':
/lib/modules/fglrx/build_mod/2.6.x/firegl_public.c:509: aviso: `inter_module_put ' is deprecated (declared at include/linux/module.h:578)
/lib/modules/fglrx/build_mod/2.6.x/firegl_public.c:511: aviso: `inter_module_unr egister' is deprecated (declared at include/linux/module.h:574)
/lib/modules/fglrx/build_mod/2.6.x/firegl_public.c: En la función `firegl_stub_r egister':
/lib/modules/fglrx/build_mod/2.6.x/firegl_public.c:531: aviso: `inter_module_reg ister' is deprecated (declared at include/linux/module.h:573)
/lib/modules/fglrx/build_mod/2.6.x/firegl_public.c:562: aviso: `inter_module_put ' is deprecated (declared at include/linux/module.h:578)
/lib/modules/fglrx/build_mod/2.6.x/firegl_public.c: En la función `firegl_get_us er_ptr':
/lib/modules/fglrx/build_mod/2.6.x/firegl_public.c:1078: aviso: asignación se cr ea un puntero desde un entero sin una conversión
/lib/modules/fglrx/build_mod/2.6.x/firegl_public.c: En la función `firegl_put_us er_ptr':
/lib/modules/fglrx/build_mod/2.6.x/firegl_public.c:1110: aviso: cast from pointe r to integer of different size
/lib/modules/fglrx/build_mod/2.6.x/firegl_public.c:1110: aviso: cast from pointe r to integer of different size
/lib/modules/fglrx/build_mod/2.6.x/firegl_public.c:1110: aviso: cast from pointe r to integer of different size
/lib/modules/fglrx/build_mod/2.6.x/firegl_public.c:1110: aviso: cast from pointe r to integer of different size
/lib/modules/fglrx/build_mod/2.6.x/firegl_public.c: En la función `__ke_get_vm_p hys_addr':
/lib/modules/fglrx/build_mod/2.6.x/firegl_public.c:1673: error: structure has no  member named `pud'
/lib/modules/fglrx/build_mod/2.6.x/firegl_public.c: En la función `do_vm_shm_nop age':
/lib/modules/fglrx/build_mod/2.6.x/firegl_public.c:2203: error: structure has no  member named `pud'
/lib/modules/fglrx/build_mod/2.6.x/firegl_public.c: En la función `__ke_vm_phys_ addr_str':
/lib/modules/fglrx/build_mod/2.6.x/firegl_public.c:2573: error: structure has no  member named `pud'
/lib/modules/fglrx/build_mod/2.6.x/firegl_public.c: En el nivel principal:
/lib/modules/fglrx/build_mod/2.6.x/firegl_public.c:2661: aviso: inicialización d e tipo de puntero incompatible
/lib/modules/fglrx/build_mod/2.6.x/firegl_public.c: En la función `__ke_vm_map':
/lib/modules/fglrx/build_mod/2.6.x/firegl_public.c:2722: aviso: implicit declara tion of function `remap_page_range'
/lib/modules/fglrx/build_mod/2.6.x/firegl_public.c: En el nivel principal:
/lib/modules/fglrx/build_mod/2.6.x/firegl_public.c:2876: error: error sintáctico  before '*' token
/lib/modules/fglrx/build_mod/2.6.x/firegl_public.c:2876: aviso: type defaults to  `int' in declaration of `drm_agp_module_stub'
/lib/modules/fglrx/build_mod/2.6.x/firegl_public.c:2876: aviso: data definition has no type or storage class
/lib/modules/fglrx/build_mod/2.6.x/firegl_public.c: En la función `__ke_agpgart_ available':
/lib/modules/fglrx/build_mod/2.6.x/firegl_public.c:3018: error: `drm_agp_t' unde clared (first use in this function)
/lib/modules/fglrx/build_mod/2.6.x/firegl_public.c:3018: error: (Each undeclared  identifier is reported only once
/lib/modules/fglrx/build_mod/2.6.x/firegl_public.c:3018: error: for each functio n it appears in.)
/lib/modules/fglrx/build_mod/2.6.x/firegl_public.c:3018: error: error sintáctico  before ')' token
/lib/modules/fglrx/build_mod/2.6.x/firegl_public.c:3039: error: request for memb er `free_memory' in something not a structure or union
/lib/modules/fglrx/build_mod/2.6.x/firegl_public.c:3041: error: request for memb er `free_memory' in something not a structure or union
/lib/modules/fglrx/build_mod/2.6.x/firegl_public.c:3044: error: request for memb er `allocate_memory' in something not a structure or union
/lib/modules/fglrx/build_mod/2.6.x/firegl_public.c:3046: error: request for memb er `allocate_memory' in something not a structure or union
/lib/modules/fglrx/build_mod/2.6.x/firegl_public.c:3049: error: request for memb er `bind_memory' in something not a structure or union
/lib/modules/fglrx/build_mod/2.6.x/firegl_public.c:3051: error: request for memb er `bind_memory' in something not a structure or union
/lib/modules/fglrx/build_mod/2.6.x/firegl_public.c:3054: error: request for memb er `unbind_memory' in something not a structure or union
/lib/modules/fglrx/build_mod/2.6.x/firegl_public.c:3056: error: request for memb er `unbind_memory' in something not a structure or union
/lib/modules/fglrx/build_mod/2.6.x/firegl_public.c:3059: error: request for memb er `enable' in something not a structure or union
/lib/modules/fglrx/build_mod/2.6.x/firegl_public.c:3061: error: request for memb er `enable' in something not a structure or union
/lib/modules/fglrx/build_mod/2.6.x/firegl_public.c:3064: error: request for memb er `acquire' in something not a structure or union
/lib/modules/fglrx/build_mod/2.6.x/firegl_public.c:3066: error: request for memb er `acquire' in something not a structure or union
/lib/modules/fglrx/build_mod/2.6.x/firegl_public.c:3069: error: request for memb er `release' in something not a structure or union
/lib/modules/fglrx/build_mod/2.6.x/firegl_public.c:3071: error: request for memb er `release' in something not a structure or union
/lib/modules/fglrx/build_mod/2.6.x/firegl_public.c:3074: error: request for memb er `copy_info' in something not a structure or union
/lib/modules/fglrx/build_mod/2.6.x/firegl_public.c:3076: error: request for memb er `copy_info' in something not a structure or union
/lib/modules/fglrx/build_mod/2.6.x/firegl_public.c: En la función `__ke_agp_unin it':
/lib/modules/fglrx/build_mod/2.6.x/firegl_public.c:3147: aviso: `inter_module_pu t' is deprecated (declared at include/linux/module.h:578)
/lib/modules/fglrx/build_mod/2.6.x/firegl_public.c: En la función `__ke_agp_free _memory':
/lib/modules/fglrx/build_mod/2.6.x/firegl_public.c:3180: error: request for memb er `free_memory' in something not a structure or union
/lib/modules/fglrx/build_mod/2.6.x/firegl_public.c:3181: error: request for memb er `free_memory' in something not a structure or union
/lib/modules/fglrx/build_mod/2.6.x/firegl_public.c: En la función `__ke_agp_allo cate_memory':
/lib/modules/fglrx/build_mod/2.6.x/firegl_public.c:3190: error: request for memb er `allocate_memory' in something not a structure or union
/lib/modules/fglrx/build_mod/2.6.x/firegl_public.c:3191: error: request for memb er `allocate_memory' in something not a structure or union
/lib/modules/fglrx/build_mod/2.6.x/firegl_public.c: En la función `__ke_agp_bind _memory':
/lib/modules/fglrx/build_mod/2.6.x/firegl_public.c:3201: error: request for memb er `bind_memory' in something not a structure or union
/lib/modules/fglrx/build_mod/2.6.x/firegl_public.c:3202: error: request for memb er `bind_memory' in something not a structure or union
/lib/modules/fglrx/build_mod/2.6.x/firegl_public.c: En la función `__ke_agp_unbi nd_memory':
/lib/modules/fglrx/build_mod/2.6.x/firegl_public.c:3212: error: request for memb er `unbind_memory' in something not a structure or union
/lib/modules/fglrx/build_mod/2.6.x/firegl_public.c:3213: error: request for memb er `unbind_memory' in something not a structure or union
/lib/modules/fglrx/build_mod/2.6.x/firegl_public.c: En la función `__ke_agp_enab le':
/lib/modules/fglrx/build_mod/2.6.x/firegl_public.c:3223: error: request for memb er `enable' in something not a structure or union
/lib/modules/fglrx/build_mod/2.6.x/firegl_public.c:3225: error: request for memb er `enable' in something not a structure or union
/lib/modules/fglrx/build_mod/2.6.x/firegl_public.c: En la función `__ke_agp_acqu ire':
/lib/modules/fglrx/build_mod/2.6.x/firegl_public.c:3271: error: request for memb er `acquire' in something not a structure or union
/lib/modules/fglrx/build_mod/2.6.x/firegl_public.c:3272: error: request for memb er `acquire' in something not a structure or union
/lib/modules/fglrx/build_mod/2.6.x/firegl_public.c: En la función `__ke_agp_rele ase':
/lib/modules/fglrx/build_mod/2.6.x/firegl_public.c:3282: error: request for memb er `release' in something not a structure or union
/lib/modules/fglrx/build_mod/2.6.x/firegl_public.c:3283: error: request for memb er `release' in something not a structure or union
/lib/modules/fglrx/build_mod/2.6.x/firegl_public.c: En la función `__ke_agp_copy _info':
/lib/modules/fglrx/build_mod/2.6.x/firegl_public.c:3296: error: request for memb er `copy_info' in something not a structure or union
/lib/modules/fglrx/build_mod/2.6.x/firegl_public.c:3303: error: request for memb er `copy_info' in something not a structure or union
make[2]: *** [/lib/modules/fglrx/build_mod/2.6.x/firegl_public.o] Error 1
make[1]: *** [_module_/lib/modules/fglrx/build_mod/2.6.x] Error 2
make[1]: Leaving directory `/usr/src/linux-2.6.11'
make: *** [kmod_build] Error 2
build failed with return value 2

```I use hoary amd64, what's wrong?
Thanks

---

### Post by tturk on 2005-03-07
[QUOTE=PeP]sudo patch -p0 < patch-fglrx-8.10.19.-1-kernel.2.6.11.txt[/QUOTE]

It did work for me, thanks. Now it compiles ok, but there was a typo in your patch on line 8, and #i**d**fdef instead of an #ifdef

---

### Post by tturk on 2005-03-08
I forgot I was on 2.6.10 while compiling with this patch.
Now I'm on 2.6.11 and I compiled the latest ati drivers with this other [patch](http://www.webdeko.com/firegl_public.patch)

---

### Post by remmelt on 2005-03-09
i did all the things as suggested and i started up x. now, how can i tell if i did it right? what's the difference?

---

### Post by bobmitch on 2005-03-09
[QUOTE=remmelt]i did all the things as suggested and i started up x. now, how can i tell if i did it right? what's the difference?[/QUOTE]

Run 'fglrxinfo'

If the OpenGL vendor string is ATI Technologies Inc. and not MesaGL (or similar) it has worked. :)

---

### Post by cyu021 on 2005-03-19
hi folks,

Just need to ask where did you get ATI Mobility's drivers?
All I got is this:
```

https://support.ati.com/ics/support/default.asp?deptID=894&task=knowledge&folderID=27

```


Thanks in advance,
James

---

