---
title: "xorg.conf custom resolution"
date: 2009-12-01
forum: General Help
---

### Post by isacdan on 2009-12-01
Hi! 

I'm having a bit of a problem with my screen resolution. I can't set it to my monitor's default (1680x1050@60). I'm using an ATI Radeon 4770 and I've also installed the latest driver. The resolution I need is not showing up in Display or Catalyst.

The thing that I'm trying to do is set a custom resolution using the xorg.conf file, but I'm not quite sure how to do this...

Any help will be appreciated... Thanks... :D

Here are the contents my xorg.conf file...


Section "ServerLayout"
    Identifier     "aticonfig Layout"
    Screen      0  "aticonfig-Screen[0]-0" 0 0
EndSection

Section "Files"
EndSection

Section "Module"
EndSection

Section "ServerFlags"
    Option        "Xinerama" "off"
EndSection

Section "Monitor"
    Identifier   "aticonfig-Monitor[0]-0"
    Option        "VendorName" "ATI Proprietary Driver"
    Option        "ModelName" "Generic Autodetecting Monitor"
    Option        "DPMS" "true"
EndSection

Section "Device"
    Identifier  "aticonfig-Device[0]-0"
    Driver      "fglrx"
    BusID       "PCI:1:0:0"
EndSection

Section "Screen"
    Identifier "aticonfig-Screen[0]-0"
    Device     "aticonfig-Device[0]-0"
    Monitor    "aticonfig-Monitor[0]-0"
    DefaultDepth     24
    SubSection "Display"
        Viewport   0 0
        Depth     24
    EndSubSection
EndSection

---

### Post by ed-koala on 2009-12-01
From this link [http://ubuntuforums.org/showpost.php?p=129379&postcount=21]("http://ubuntuforums.org/showpost.php?p=129379&postcount=21") comes this:

```
Section "Screen"
    Identifier    "Default Screen"
    Device        "NVIDIA Corporation NV34 [GeForce FX 5200]"
    Monitor        "CM752ET"
    DefaultDepth    16
    [B]SubSection "Display":
        Depth        16
        Modes      "1280x1024" "1024x768"
    EndSubSection[/B]
EndSection
```

Note the part in bold, that'll be your custom resolution. I noticed yours is a depth of 24 so make sure you edit things properly. And obviosly the resolution is different too.

---

### Post by isacdan on 2009-12-01
I've already tries that...
When I run in the terminal "sudo gedit /etc/x11/xorg.conf", the xorg.conf file is opened, but it's empty and I can't write anything in it. I get a similar result with "sudo nano /etc/x11/xorg.conf"... I don't know if I'm doing something wrong...

---

### Post by ed-koala on 2009-12-01
Karmic doesn't have an xorg.conf by default, but if you create one it should use it.

Also, the directory is X11, not x11.  Makes a difference. :)

---

### Post by Nylo on 2009-12-01
> **ed-koala said:**
> Karmic doesn't have an xorg.conf by default, but if you create one it should use it.

Also, the directory is X11, not x11.  Makes a difference. :)

How does one create a, xorg.conf file?  

I'm new so treat me like Forest Gump.

---

### Post by audiomick on 2009-12-01
Hallo.
I would suggest you look at this:
[https://wiki.ubuntu.com/X/Config/Resolution](https://wiki.ubuntu.com/X/Config/Resolution)

and look at the man page, as suggested on the above mentioned page, for xorg.config

```
man xorg.conf
```

I had to get into this a few years ago when Linux still didn't support 1280 x 800 out of the box. It actually isn't that hard, it is just a heap of stuff to wade through to get at what you need.

---

### Post by Nylo on 2009-12-01
> **audiomick said:**
> Hallo.
I would suggest you look at this:
[https://wiki.ubuntu.com/X/Config/Resolution](https://wiki.ubuntu.com/X/Config/Resolution)

and look at the man page, as suggested on the above mentioned page, for xorg.config

```
man xorg.conf
```

I had to get into this a few years ago when Linux still didn't support 1280 x 800 out of the box. It actually isn't that hard, it is just a heap of stuff to wade through to get at what you need.

Obviously you didn't see the movie, Forest Gump.  Its a movie about an idiot.  Now that this is cleared up, "man xorg.conf" states nothing about how to create a Xorg.conf file...  Just explains it.

Now, with the key word here being idiot ie. me, how do you create a Xorg.conf file so I can get my beloved 1024x768 back.

---

### Post by ed-koala on 2009-12-01
See this:

[http://www.cyberciti.biz/tips/create-a-xorgconf-file.html]("http://www.cyberciti.biz/tips/create-a-xorgconf-file.html")

Run Forrest, run!

---

### Post by Nylo on 2009-12-02
> **ed-koala said:**
> See this:

[http://www.cyberciti.biz/tips/create-a-xorgconf-file.html]("http://www.cyberciti.biz/tips/create-a-xorgconf-file.html")

Run Forrest, run!

I tried this but I get an error.
[B]
"Server is already active for display 0
If this server is no longer running, remove /tmp/ .X0-lock"[/B]

Problem is I do not have .X0-lock.

---

### Post by ed-koala on 2009-12-02
Okj, this was yesterday so my brain dumped all this info, let's refresh ...

Right now, does the file /etc/X11/xorg.conf exist?

If yes, copy and paste output here.

If no, open a terminal and run the following command:

```
sudo Xorg -configure
```

Then go back and check to see if /etc/X11/xorg.conf exists, and as it now should, copy and paste it here.

DO NOT REBOOT!!!  Because you have restricted drivers installed, you may end up not having a GUI if you do at this point.  We need to do some editing/configuring first to xorg.conf

---

### Post by Nylo on 2009-12-02
> **ed-koala said:**
> Okj, this was yesterday so my brain dumped all this info, let's refresh ...

Right now, does the file /etc/X11/xorg.conf exist?

If yes, copy and paste output here.

If no, open a terminal and run the following command:

```
sudo Xorg -configure
```

Then go back and check to see if /etc/X11/xorg.conf exists, and as it now should, copy and paste it here.

DO NOT REBOOT!!!  Because you have restricted drivers installed, you may end up not having a GUI if you do at this point.  We need to do some editing/configuring first to xorg.conf

No I do not have, "/etc/X11/xorg.conf" and Im getting the same error.   :(

---

### Post by ed-koala on 2009-12-02
Hmmm, I'm not familiar with that error. Hopefully someone else better versed with xorg can step in and suggest what to do.

---

### Post by isacdan on 2009-12-23
Hi!
I finally managed to set the 1680x1050 resolution by modifying xorg.conf. However, it seems to work only after creating it. Installing the graphics card's driver modifies xorg.conf again, the desired resolution becoming unavailable.

What I did was reinstall Ubuntu and start fresh. First, I got the modeline for my monitor,
```
cvt 1680 1050 60
```obtaining the following output:
```

Modeline "1680x1050_60.00"  146.25  1680 1784 1960 2240  1050 1053 1059 1089 -hsync +vsync
```Then, I created a new xorg.conf file:
```
sudo /etc/init.d/gdm stop
sudo Xorg -configure
sudo /etc/init.d/gdm start
```The "Xorg -configure" generated a xorg.conf.new file somewhere in the home folder (I don't remember where exactly, but its location was printed on screen). I copied the xorg.conf.new file in /etc/X11/xorg.conf.
```
sudo cp <insert_xorg.conf.new_location_here> /etc/X11/xorg.conf
```I opened xorg.conf:
```
sudo gedit /etc/X11/cong.conf
```I added the Modeline generated earlier under the "Monitor" Section and the <Modes "1680x1050">  line under the "Screen" section, SubSection "Display", under the Depth 24 line.

I saved the file, rebooted and it worked... until I installed the graphics card driver, which brought me right back where I started.

Here is what the xorg.conf file that Xorg -configure generated:
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
    Load  "glx"
    Load  "extmod"
    Load  "dbe"
    Load  "dri"
EndSection

Section "InputDevice"
    Identifier  "Keyboard0"
    Driver      "kbd"
EndSection

Section "InputDevice"
    Identifier  "Mouse0"
    Driver      "mouse"
    Option        "Protocol" "auto"
    Option        "Device" "/dev/input/mice"
    Option        "ZAxisMapping" "4 5 6 7"
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
        #Option     "NoAccel"                # [<bool>]
        #Option     "SWcursor"               # [<bool>]
        #Option     "Dac6Bit"                # [<bool>]
        #Option     "Dac8Bit"                # [<bool>]
        #Option     "BusType"                # [<str>]
        #Option     "CPPIOMode"              # [<bool>]
        #Option     "CPusecTimeout"          # <i>
        #Option     "AGPMode"                # <i>
        #Option     "AGPFastWrite"           # [<bool>]
        #Option     "AGPSize"                # <i>
        #Option     "GARTSize"               # <i>
        #Option     "RingSize"               # <i>
        #Option     "BufferSize"             # <i>
        #Option     "EnableDepthMoves"       # [<bool>]
        #Option     "EnablePageFlip"         # [<bool>]
        #Option     "NoBackBuffer"           # [<bool>]
        #Option     "DMAForXv"               # [<bool>]
        #Option     "FBTexPercent"           # <i>
        #Option     "DepthBits"              # <i>
        #Option     "PCIAPERSize"            # <i>
        #Option     "AccelDFS"               # [<bool>]
        #Option     "IgnoreEDID"             # [<bool>]
        #Option     "DisplayPriority"        # [<str>]
        #Option     "PanelSize"              # [<str>]
        #Option     "ForceMinDotClock"       # <freq>
        #Option     "ColorTiling"            # [<bool>]
        #Option     "VideoKey"               # <i>
        #Option     "RageTheatreCrystal"     # <i>
        #Option     "RageTheatreTunerPort"     # <i>
        #Option     "RageTheatreCompositePort"     # <i>
        #Option     "RageTheatreSVideoPort"     # <i>
        #Option     "TunerType"              # <i>
        #Option     "RageTheatreMicrocPath"     # <str>
        #Option     "RageTheatreMicrocType"     # <str>
        #Option     "ScalerWidth"            # <i>
        #Option     "RenderAccel"            # [<bool>]
        #Option     "SubPixelOrder"          # [<str>]
        #Option     "ShowCache"              # [<bool>]
        #Option     "ClockGating"            # [<bool>]
        #Option     "VGAAccess"              # [<bool>]
        #Option     "ReverseDDC"             # [<bool>]
        #Option     "LVDSProbePLL"           # [<bool>]
        #Option     "AccelMethod"            # <str>
        #Option     "DRI"                    # [<bool>]
        #Option     "ConnectorTable"         # <str>
        #Option     "DefaultConnectorTable"     # [<bool>]
        #Option     "DefaultTMDSPLL"         # [<bool>]
        #Option     "TVDACLoadDetect"        # [<bool>]
        #Option     "ForceTVOut"             # [<bool>]
        #Option     "TVStandard"             # <str>
        #Option     "IgnoreLidStatus"        # [<bool>]
        #Option     "DefaultTVDACAdj"        # [<bool>]
        #Option     "Int10"                  # [<bool>]
        #Option     "EXAVSync"               # [<bool>]
        #Option     "ATOMTVOut"              # [<bool>]
        #Option     "R4xxATOM"               # [<bool>]
        #Option     "ForceLowPowerMode"      # [<bool>]
        #Option     "DynamicPM"              # [<bool>]
    Identifier  "Card0"
    Driver      "radeon"
    VendorName  "ATI Technologies Inc"
    BoardName   "Radeon HD 4770 [RV740]"
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

```This is what it looked like after I added those line (the lines added by me are in red and bold)>
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
    Load  "glx"
    Load  "extmod"
    Load  "dbe"
    Load  "dri"
EndSection

Section "InputDevice"
    Identifier  "Keyboard0"
    Driver      "kbd"
EndSection

Section "InputDevice"
    Identifier  "Mouse0"
    Driver      "mouse"
    Option        "Protocol" "auto"
    Option        "Device" "/dev/input/mice"
    Option        "ZAxisMapping" "4 5 6 7"
EndSection

Section "Monitor"
    Identifier   "Monitor0"
    VendorName   "Monitor Vendor"
    ModelName    "Monitor Model"
    [COLOR="Red"]**Modeline "1680x1050_60.00"  146.25  1680 1784 1960 2240  1050 1053 1059 1089 -hsync +vsync**[/COLOR]
EndSection

Section "Device"
        ### Available Driver options are:-
        ### Values: <i>: integer, <f>: float, <bool>: "True"/"False",
        ### <string>: "String", <freq>: "<f> Hz/kHz/MHz"
        ### [arg]: arg optional
        #Option     "NoAccel"                # [<bool>]
        #Option     "SWcursor"               # [<bool>]
        #Option     "Dac6Bit"                # [<bool>]
        #Option     "Dac8Bit"                # [<bool>]
        #Option     "BusType"                # [<str>]
        #Option     "CPPIOMode"              # [<bool>]
        #Option     "CPusecTimeout"          # <i>
        #Option     "AGPMode"                # <i>
        #Option     "AGPFastWrite"           # [<bool>]
        #Option     "AGPSize"                # <i>
        #Option     "GARTSize"               # <i>
        #Option     "RingSize"               # <i>
        #Option     "BufferSize"             # <i>
        #Option     "EnableDepthMoves"       # [<bool>]
        #Option     "EnablePageFlip"         # [<bool>]
        #Option     "NoBackBuffer"           # [<bool>]
        #Option     "DMAForXv"               # [<bool>]
        #Option     "FBTexPercent"           # <i>
        #Option     "DepthBits"              # <i>
        #Option     "PCIAPERSize"            # <i>
        #Option     "AccelDFS"               # [<bool>]
        #Option     "IgnoreEDID"             # [<bool>]
        #Option     "DisplayPriority"        # [<str>]
        #Option     "PanelSize"              # [<str>]
        #Option     "ForceMinDotClock"       # <freq>
        #Option     "ColorTiling"            # [<bool>]
        #Option     "VideoKey"               # <i>
        #Option     "RageTheatreCrystal"     # <i>
        #Option     "RageTheatreTunerPort"     # <i>
        #Option     "RageTheatreCompositePort"     # <i>
        #Option     "RageTheatreSVideoPort"     # <i>
        #Option     "TunerType"              # <i>
        #Option     "RageTheatreMicrocPath"     # <str>
        #Option     "RageTheatreMicrocType"     # <str>
        #Option     "ScalerWidth"            # <i>
        #Option     "RenderAccel"            # [<bool>]
        #Option     "SubPixelOrder"          # [<str>]
        #Option     "ShowCache"              # [<bool>]
        #Option     "ClockGating"            # [<bool>]
        #Option     "VGAAccess"              # [<bool>]
        #Option     "ReverseDDC"             # [<bool>]
        #Option     "LVDSProbePLL"           # [<bool>]
        #Option     "AccelMethod"            # <str>
        #Option     "DRI"                    # [<bool>]
        #Option     "ConnectorTable"         # <str>
        #Option     "DefaultConnectorTable"     # [<bool>]
        #Option     "DefaultTMDSPLL"         # [<bool>]
        #Option     "TVDACLoadDetect"        # [<bool>]
        #Option     "ForceTVOut"             # [<bool>]
        #Option     "TVStandard"             # <str>
        #Option     "IgnoreLidStatus"        # [<bool>]
        #Option     "DefaultTVDACAdj"        # [<bool>]
        #Option     "Int10"                  # [<bool>]
        #Option     "EXAVSync"               # [<bool>]
        #Option     "ATOMTVOut"              # [<bool>]
        #Option     "R4xxATOM"               # [<bool>]
        #Option     "ForceLowPowerMode"      # [<bool>]
        #Option     "DynamicPM"              # [<bool>]
    Identifier  "Card0"
    Driver      "radeon"
    VendorName  "ATI Technologies Inc"
    BoardName   "Radeon HD 4770 [RV740]"
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
        [COLOR="Red"]**Modes "1680x1050"**[/COLOR]
    EndSubSection
EndSection

```

So... Does anyone know a way to keep the desired resolution after installing the ATI restricted drivers?

Happy Holidays, everyone! :biggrin:

---

