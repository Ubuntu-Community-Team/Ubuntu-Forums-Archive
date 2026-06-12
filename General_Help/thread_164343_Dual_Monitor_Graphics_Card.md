---
title: "Dual Monitor Graphics Card"
date: 2006-04-22
forum: General Help
---

### Post by nami on 2006-04-22
Hi

I would like to give Ubuntu another try.  However my hardware has slightly changed.  I've JUST started downloading the DVD image again as I lost the old one and its estimated completion time is 3 hours!!!

Anyway, still have my original GeForce 4200 Ti graphics card, but now ALSO have 2 19" monitors @ 1280 1024 each.  These monitors work perfectly with Windows XP.

So my question is, will Ubuntu recognise the 2 monitors and allow me to use both monitors as an extended desktop across both?

Any advice will be appreciated.

nami.

---

### Post by aqua on 2006-04-22
Plug both monitors in then use the command lspci. Note the busid's before any information about displays. I get this:

0000:01:00.0 VGA compatible controller: ATI Technologies Inc Radeon R350 [Radeon 9800 Pro]
0000:01:00.1 Display controller: ATI Technologies Inc Radeon R350 [Radeon 9800 Pro] (Secondary)

So that's bus id 1.0.0 and 1.0.1 for the two displays. Then read this:

[http://www.ubuntuforums.org/showthread.php?t=163053](http://www.ubuntuforums.org/showthread.php?t=163053)

Especially the messages at the end of the thread.

---

### Post by djsroknrol on 2006-04-22
What driver are you using?...If it's an oss driver, give this link a try:

[This link]("http://ubuntuforums.org/showthread.php?t=163982&highlight=span+monitors+vertically")

I think this will help you...

---

### Post by nami on 2006-04-23
I havnt installed ubuntu 5.10 yet!  So how do I find out which driver I need?

---

### Post by nami on 2006-05-06
I have just installed a fresh copy of breezy.  What do I do next?  Do I follow the information on the links above, or do I install the nVidia drivers first?

---

### Post by nami on 2006-05-06
I have installed the nVidia graphics drivers, but am still not getting 2 monitors.  I know I have installed the driver properly bacause I get the nVidia logo when I start the computer.  I followed the instructions on the following page to install the driver:

I use Method 2 on the following page:
[http://ubuntuforums.org/showthread.php?t=75074](http://ubuntuforums.org/showthread.php?t=75074)

I typed in > lspci | grep VGA and got the following output:

> nami@ubuntu:~$ lspci | grep VGA
0000:01:00.0 VGA compatible controller: nVidia Corporation NV25 [GeForce4 Ti 4200] (rev a3)
nami@ubuntu:~$

What do I do next?

Please help.

---

### Post by bunnieofdoom on 2006-05-06
sudo apt-get install nvidia-glx

sudo dpkg-reconfigure xserver-xorg

uncheck nv check nvidia

sudo gedit /etc/X11/xorg.conf



add these lines under Section "Device"
	Identifier	"your nvidia card here"
	Driver		"nvidia"
	BusID		"PCIblahbalhblah"
<add these>	Option "TwinView" "true"
	Option "TwinViewOrientation" "Clone"
	Option "TVOutFormat" "S-VIDEO"
	Option "TVStandard" "NTSC-M"
	Option "SecondMonitorHorizSync" "30-50"
	Option "SecondMonitorVertRefresh" "60"
	Option "MetaModes" "1024x768,1024x768;800x600,800x600;640x480,640x480;    512x384,512x384"</addthese>
EndSection

hope this helps :)

---

### Post by nami on 2006-05-06
Before I do this, will this give me an extended desktop or an mirror desktop?  I'm after an extended desktop.

Also I currently have my monitors at 1280 x 1024 each.

---

### Post by bunnieofdoom on 2006-05-06
Option "TwinViewOrientation" "Clone"

will give you a mirror ill google around real quick and look for extended

---

### Post by bunnieofdoom on 2006-05-06
[http://www.ublug.org/ubuntu/twinview/twinview-howto-breezy.html](http://www.ublug.org/ubuntu/twinview/twinview-howto-breezy.html)


good howto :)

---

### Post by nami on 2006-05-06
Your instructions in post seven killed my ubuntu install!  It is now complaining about unable to start x window or something.

I had a feeling it wouldnt work, because to get my graphics card to work i had to uninstall nvidia-glx.

So what do I do now?

---

### Post by bunnieofdoom on 2006-05-06
post the error output of xserver please. also are you running a custom kernel?

---

### Post by nami on 2006-05-06
Ok, I've done another fresh install of ubuntu and have installed the following nVidia drivers

NVIDIA-Linux-x86-1.0-8756-pkg1.run

To install the nvidia drivers, I followed the "method 2" instructions from this page: [http://ubuntuforums.org/showthread.php?t=75074](http://ubuntuforums.org/showthread.php?t=75074).

You told me to follow the following page: [http://www.ublug.org/ubuntu/twinview/twinview-howto-breezy.html](http://www.ublug.org/ubuntu/twinview/twinview-howto-breezy.html)

But that page says > Using Synaptic install the following packages: nvidia-glx, the linux-restricted-modules (choose the one that matches your kernel) and nvidia-settings

When I followed the instruction the first link to install the nVidia drivers, I was told to remove nvidia-glx.

Anyway, I went to Synaptic and searched for nvidia-glx and it brings up version 1.0.7667.  This version is COMPLETELY different from the graphics driver I have installed right now which is 1.0.8756.  When I did install it before using your instructions, it ruined my ubuntu install.  So do I have to install this to follow the instructions on the following page? [http://www.ublug.org/ubuntu/twinview/twinview-howto-breezy.html](http://www.ublug.org/ubuntu/twinview/twinview-howto-breezy.html)

nami

---

### Post by nami on 2006-05-07
I currently have the following in the "Device" section in my xorg.conf

Section "Device"
    Identifier     "NVIDIA Corporation NV25 [GeForce4 Ti 4200]"
    Driver         "nvidia"
EndSection

But I need to change it to something like this:

Section "Device"
Identifier "NVIDIA Corporation NV43 [GeForce 6600/GeForce 6600 Ultra]"
Driver "nvidia"
VendorName "Videocard vendor"
BoardName "NVIDIA GeForce 6600 GT"
BusID "PCI:1:5:0"
Option "NvAGP" "2"
Option "NoLogo" "1"
Option "RenderAccel" "0"
Option "CursorShadow" "1"
Option "Coolbits" "1"
Option "ConnectedMonitor" "dfp, dfp"
Option "NoPowerConnectorCheck"
Option "TwinView" "1"
Option "Metamodes" "1280x1024,1280x1024; 1024x768,1024x768; 1280x1024,NULL; 1024x768,NULL"
Option "SecondMonitorHorizSync" "31-82"
Option "SecondMonitorVertRefresh" "56-76"
# Option "NoTwinViewXineramaInfo"
EndSection

I have a GeForce Ti 4200 instead or a GeForce 6600 and I don't know what values to put in for

VendorName
BoardName
BusID
ConnectedMonitor
SecondMonitorHorizSync
SecondMonitorVertRefresh

How do I find out these values?

Thanks

---

### Post by nami on 2006-05-07
Ok, I got both monitors working, I can drag windows across both monitors and also icons.

Here is a pic (Click to enlarge)
[[IMG]http://img242.imageshack.us/img242/6361/screenshot8kz.th.jpg[/IMG]](http://img242.imageshack.us/img242/6361/screenshot8kz.jpg)

As you can see the bars are the top and bottom are not extending to the second monitor.  How do you to that?

---

### Post by nami on 2006-05-07
Nevermind, got it working!

Click to enlarge:
[[IMG]http://img344.imageshack.us/img344/1940/screenshot28wu.th.jpg[/IMG]](http://img344.imageshack.us/img344/1940/screenshot28wu.jpg)

Thanks for the link bunnieofdoom.

---

### Post by bunnieofdoom on 2006-05-07
lol no worries i was trying to recreate the problem on my p3 box but im glad you fixed it lol :)

---

### Post by SuseZ on 2006-05-07
[QUOTE=nami]
VendorName
BoardName
BusID
ConnectedMonitor
SecondMonitorHorizSync
SecondMonitorVertRefresh

How do I find out these values?

Thanks[/QUOTE]

How do you find that values?

And can you show us your final xorg.conf file please?

thank you

---

### Post by nami on 2006-05-07
VendorName and BoardName are just labels so you can type whatever you like.

For the BusID I opened the terminal and typed 

 > lspci | grep VGA

 and looked at the VGA compatible controller line.  For me it was 01:00.0 so in the xorg.conf I used > BusID "PCI:1:0:0"

ConnectedMonitor depends on your monitor ports, if they are dvi you need to type:
 > Option "ConnectedMonitor" "dfp, dfp"

if they are analog you type
 > Option "ConnectedMonitor" "ctr, ctr"

The first one is for your main monitor and the second one is for your second monitor.  If you have mixed monitors you change the values in the quotes to reflect your monitors e.g.

 > Option "ConnectedMonitor" "dfp, ctr"
so this is saying that your first monitor is dvi and your second monitor is analog

And for:
> SecondMonitorHorizSync
SecondMonitorVertRefresh

You have to google or look in your monitor instructions.

Here is my xorg.conf

> # nvidia-xconfig: X configuration file generated by nvidia-xconfig
# nvidia-xconfig:  version 1.0  (buildmeister@builder3)  Wed Mar 29 14:43:26 PST 2006

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

Section "ServerLayout"
    Identifier     "TwinView Configuration"
    Screen         0 "Default Screen" 0 0
    InputDevice    "Generic Keyboard"
    InputDevice    "Configured Mouse"
    Option	   "Xinerama" "Off"
EndSection

Section "Files"

        # paths to defoma fonts
    FontPath        "/usr/share/X11/fonts/misc"
    FontPath        "/usr/share/X11/fonts/cyrillic"
    FontPath        "/usr/share/X11/fonts/100dpi/:unscaled"
    FontPath        "/usr/share/X11/fonts/75dpi/:unscaled"
    FontPath        "/usr/share/X11/fonts/Type1"
    FontPath        "/usr/share/X11/fonts/CID"
    FontPath        "/usr/share/X11/fonts/100dpi"
    FontPath        "/usr/share/X11/fonts/75dpi"
    FontPath        "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
    FontPath        "/var/lib/defoma/x-ttcidfont-conf.d/dirs/CID"
EndSection

Section "Module"
    Load           "i2c"
    Load           "bitmap"
    Load           "ddc"
    Load           "extmod"
    Load           "freetype"
    Load           "glx"
    Load           "int10"
    Load           "type1"
    Load           "vbe"
EndSection

Section "InputDevice"
    Identifier     "Generic Keyboard"
    Driver         "kbd"
    Option         "CoreKeyboard"
    Option         "XkbRules" "xorg"
    Option         "XkbModel" "pc105"
    Option         "XkbLayout" "gb"
EndSection

Section "InputDevice"
    Identifier     "Configured Mouse"
    Driver         "mouse"
    Option         "CorePointer"
    Option         "Device" "/dev/input/mice"
    Option         "Protocol" "ImPS/2"
    Option         "Emulate3Buttons" "true"
    Option         "ZAxisMapping" "4 5"
EndSection

Section "Monitor"
    Identifier     "AL1916"
    Option         "DPMS"
EndSection

Section "Device"
    Identifier     "NVIDIA Corporation NV25 [GeForce4 Ti 4200]"
    Driver         "nvidia"
    VendorName     "Videocard vendor"
    BoardName      "NVIDIA GeForce4 Ti 4200"
    BusID          "PCI:1:0:0"
    Option         "NvAGP" "2"
    Option         "NoLogo" "1"
    Option         "RenderAccel" "0"
    Option         "CursorShadow" "1"
    Option         "Coolbits" "1"
    Option         "ConnectedMonitor" "ctr, ctr"
    Option         "NoPowerConnectorCheck"
    Option         "TwinView" "1"
    Option         "Metamodes" "1280x1024,1280x1024; 1024x768,1024x768; 1280x1024,NULL; 1024x768,NULL"
    Option         "SecondMonitorHorizSync" "30-65"
    Option         "SecondMonitorVertRefresh" "50-75"
    # Option "NoTwinViewXineramaInfo"
EndSection

Section "Screen"
    Identifier     "Default Screen"
    Device         "NVIDIA Corporation NV25 [GeForce4 Ti 4200]"
    Monitor        "AL1916"
    DefaultDepth    24
    SubSection     "Display"
        Viewport    0 0
        Depth       1
        Modes      "1280x1024" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
    EndSubSection
    SubSection     "Display"
        Viewport    0 0
        Depth       4
        Modes      "1280x1024" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
    EndSubSection
    SubSection     "Display"
        Viewport    0 0
        Depth       8
        Modes      "1280x1024" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
    EndSubSection
    SubSection     "Display"
        Viewport    0 0
        Depth       15
        Modes      "1280x1024" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
    EndSubSection
    SubSection     "Display"
        Viewport    0 0
        Depth       16
        Modes      "1280x1024" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
    EndSubSection
    SubSection     "Display"
        Viewport    0 0
        Depth       24
        Modes      "1280x1024" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
    EndSubSection
EndSection



If you need help any further help, let me know.

---

### Post by SuseZ on 2006-05-07
[QUOTE=nami]
You have to google or look in your monitor instructions.
[/QUOTE]
I have a very old and strange monitor, but anyway it works correctly if I don't set the  sync values.

My problem is that I only get a clone in both monitors, and I'd like have an extended desktop like your first thumbnail, and drag windows across both monitors, having the bars only in the default monitor. 

I think my conf file is alike yours:
```

# nvidia-xconfig: X configuration file generated by nvidia-xconfig
# nvidia-xconfig:  version 1.0  (buildmeister@builder3)  Wed Mar 29 14:43:26 PST 2006

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

Section "ServerLayout"
    Identifier     "Default Layout"
    Screen         0 "Default Screen" 0 0
    InputDevice    "Generic Keyboard"
    InputDevice    "Configured Mouse"
    Option         "Xinerama" "Off"
EndSection

Section "Files"

        # paths to defoma fonts
    FontPath        "/usr/share/X11/fonts/misc"
    FontPath        "/usr/share/X11/fonts/cyrillic"
    FontPath        "/usr/share/X11/fonts/100dpi/:unscaled"
    FontPath        "/usr/share/X11/fonts/75dpi/:unscaled"
    FontPath        "/usr/share/X11/fonts/Type1"
    FontPath        "/usr/share/X11/fonts/CID"
    FontPath        "/usr/share/X11/fonts/100dpi"
    FontPath        "/usr/share/X11/fonts/75dpi"
    FontPath        "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
    FontPath        "/var/lib/defoma/x-ttcidfont-conf.d/dirs/CID"
EndSection

Section "Module"
    Load           "i2c"
    Load           "bitmap"
    Load           "ddc"
    Load           "extmod"
    Load           "freetype"
    Load           "glx"
    Load           "int10"
    Load           "type1"
    Load           "vbe"
EndSection

Section "InputDevice"
    Identifier     "Generic Keyboard"
    Driver         "kbd"
    Option         "CoreKeyboard"
    Option         "XkbRules" "xorg"
    Option         "XkbModel" "pc105"
    Option         "XkbLayout" "es"
EndSection

Section "InputDevice"
    Identifier     "Configured Mouse"
    Driver         "mouse"
    Option         "CorePointer"
    Option         "Device" "/dev/input/mice"
    Option         "Protocol" "ImPS/2"
    Option         "Emulate3Buttons" "true"
    Option         "ZAxisMapping" "4 5"
EndSection

Section "Monitor"
    Identifier     "DiamondPlus7"
    Option         "DPMS"
EndSection

Section "Device"
    Identifier     "NVIDIA Corporation NV11 [GeForce2 MX/MX 400]"
    Driver         "nvidia"
    BusID          "PCI:1:0:0"
    Option         "NvAGP" "2"
    Option         "NoLogo" "1"
    Option         "RenderAccel" "0"
    Option         "ConnectedMonitor" "crt, crt"
    Option         "NoPowerConnectorCheck"
    Option         "TwinView" "1"
    Option 	   "TwinViewOrientation" "LeftOf"
    #Option "NoTwinViewXineramaInfo"
    Option         "Metamodes" "1024x768,1024x768; 800x600,800x600; 800x600,NULL; 1024x768,NULL"
EndSection

Section "Screen"
    Identifier     "Default Screen"
    Device         "NVIDIA Corporation NV11 [GeForce2 MX/MX 400]"
    Monitor        "DiamondPlus7"
    DefaultDepth    24

    SubSection     "Display"
        Depth       1
        Modes      "1280x1024" "1024x768" "800x600" "720x400" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       4
        Modes      "1280x1024" "1024x768" "800x600" "720x400" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       8
        Modes      "1280x1024" "1024x768" "800x600" "720x400" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       15
        Modes      "1280x1024" "1024x768" "800x600" "720x400" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       16
        Modes      "1280x1024" "1024x768" "800x600" "720x400" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       24
        Modes      "1280x1024" "1024x768" "800x600" "720x400" "640x480"
    EndSubSection
EndSection

```

Where I am wrong?

---

### Post by nami on 2006-05-07
I've has a quick look at your xorg.conf and you need to add

>  Viewport 0 0

to each sub section of the "screen" section.

Have a look at my xorg.conf to see what I mean.

---

### Post by Scunizi on 2006-05-07
And there is another way for Susez.  I set mine up last night.  I've got a 17"CRT for the first monitor and a 19" DVI for the second.  I wanted my panels on the 1st and the second for dragging applications/windows to as I need.  For some reason the information I read up on implied Twinview wasn't the option I wanted.  Here's my xorg.conf for comparison.  I haven't figured out yet how to paste something into a box w/ slider bar on this forum yet...... 

Section "ServerLayout"
 Identifier	"xinerama"
 Screen	0 "Screen0"
 Screen	1 "Screen1" RightOf "Screen0"
 InputDevice    "Generic Keyboard"
 InputDevice    "Configured Mouse"
 Option "Xinerama" "1"
EndSection

Section "Files"

 # path to defoma fonts
 FontPath        "/usr/share/X11/fonts/misc"
 FontPath        "/usr/share/X11/fonts/cyrillic"
 FontPath        "/usr/share/X11/fonts/100dpi/:unscaled"
 FontPath        "/usr/share/X11/fonts/75dpi/:unscaled"
 FontPath        "/usr/share/X11/fonts/Type1"
 FontPath        "/usr/share/X11/fonts/100dpi"
 FontPath        "/usr/share/X11/fonts/75dpi"
 FontPath        "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
EndSection

Section "Module"
 Load           "i2c"
 Load           "bitmap"
 Load           "ddc"
 Load           "extmod"
 Load           "freetype"
 Load           "glx"
 Load           "int10"
 Load           "type1"
 Load           "vbe"
EndSection

Section "InputDevice"
 Identifier     "Generic Keyboard"
 Driver         "kbd"
 Option         "CoreKeyboard"
 Option         "XkbRules" "xorg"
 Option         "XkbModel" "pc104"
 Option         "XkbLayout" "us"
EndSection

Section "InputDevice"
 Identifier     "Configured Mouse"
 Driver         "mouse"
 Option         "CorePointer"
 Option         "Device" "/dev/input/mice"
 Option         "Protocol" "ExplorerPS/2"
 Option         "ZAxisMapping" "4 5"
 Option         "Emulate3Buttons" "true"
EndSection

Section "Extensions"
 Option "Composite" "Enable"
EndSection


Section "Monitor"
 Identifier	"Envision"
 Option	"dpms"
 HorizSync 30.0-81.0
 VertRefresh 56-75
EndSection

Section "Monitor"
 Identifier	"HSD HN199D"
 Option	"dpms"
 HorizSync 30.0-98.0
 VertRefresh 50-160
EndSection

Section "Device"
    Identifier  "Nvidia0"
    VendorName  "PNY"
    BoardName   "GeForce 6600 GT"
    Driver      "nvidia"
    BusID       "PCI:1:0:0"
    Screen       0
 #SINCE NVIDIA VERSION 1.0-8756 YOU MUST USE UseDisplayDevice INSTEAD OF ConnectedMonitor TO GET XINERAMA WORK:
    #Option "ConnectedMonitor" "CRT"
    Option "UseDisplayDevice" "CRT"
    Option "NoLogo" "0"
    Option "RenderAccel" "true"
    Option "AllowGLXWithComposite" "true"
    Option "UseEdidDpi" "FALSE"
EndSection

Section "Device"
    Identifier  "Nvidia1"
    VendorName  "PNY"
    BoardName   "GeForce 6600 GT"
    Driver      "nvidia"
    BusID       "PCI:1:0:0"
    Screen       1
    #SINCE NVIDIA VERSION 1.0-8756 YOU MUST USE UseDisplayDevice INSTEAD OF ConnectedMonitor TO GET XINERAMA WORK:
    #Option "ConnectedMonitor" "DFP"
    Option "UseDisplayDevice" "DFP"
    Option "NoLogo" "0"
    Option "RenderAccel" "true"
    Option "AllowGLXWithComposite" "true"
    Option "UseEdidDpi" "FALSE"
EndSection

Section "Screen"
    Identifier	"Screen0"
    Device	"Nvidia0"
    Monitor	"Envision"
    DefaultDepth 24
    Subsection "Display"
        Depth 24
        Modes "1280x1024" "1024x768" "800x600"
    EndSubsection
EndSection

Section "Screen"
    Identifier	"Screen1"
    Device	"Nvidia1"
    Monitor	"HSD HN199D"
    DefaultDepth 24
    Subsection "Display"
        Depth 24
        Modes "1280x1024" "1024x768" "800x600"
    EndSubsection
EndSection

---

### Post by SuseZ on 2006-05-07
[QUOTE=nami]I've has a quick look at your xorg.conf and you need to add



to each sub section of the "screen" section.

Have a look at my xorg.conf to see what I mean.[/QUOTE]

Ok I didn't saw that but it doesn't work for me either.

But then I tried the Scunizi's way and it works perfectly as I want!!!

Thank you all

---

### Post by SuseZ on 2006-05-07
[QUOTE=Scunizi]
I haven't figured out yet how to paste something into a box w/ slider bar on this forum yet...... 
[/QUOTE]
Oh and you can do it clicking in the # button over the text area and wrinting into the markups, a bit more easy than configuring the dual display :D

---

### Post by Scunizi on 2006-05-07
```
THANKS!  Now I'm off to break my new dual monitor setup
with Compiz.  You'll probably see me screaming for help on another 
thread later because Compiz doesn't really support Dual monitors 
as yet... at least that's what I've read sofar.  But it looks REALLY 
cool if you like eyecandy!
```

---

