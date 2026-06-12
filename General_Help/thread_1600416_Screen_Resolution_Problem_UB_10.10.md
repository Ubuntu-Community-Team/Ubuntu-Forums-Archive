---
title: "Screen Resolution Problem UB 10.10"
date: 2010-10-18
forum: General Help
---

### Post by rockytoprsf on 2010-10-18
I have a custom PC with a (nVidia Corporation NV18 [GeForce4 MX 440 AGP 8x] (rev c1)) graphics card and a 17" Compaq MV720 CRT monitor. My graphics card/monitor combination is capable of resolutions up to 1280 X 1024.

I just installed Ubuntu 10.10 64Bit, and the highest resolution available at Sysytem>Preferences>Monitors>Resolution: is 1024 X 768. I want to get the resolution up to 1152 X 864, which the card/monitor is capable of. I looked around the forum for a solution, but couldn't find a thread that explains exactly what I want to do. In the most previous version of Ubuntu that I used (9.10), I could generate an xorg.conf with Xorg, grab the (Monitor, Device, and Screen) sections, and use that with a few changes to create an xorg.conf to get the resolutions that I wanted. In 10.10, that no longer works. In fact, it won't even work without the changes. After placing the xorg.conf in /etc/X11, the PC will only boot up to a text CLI prompt to login. No GUI desktop.

My PC is a totally orthodox desktop, no dual boot, no Virtualbox. What do I have to do to get the resolutions above 1024 X 768?

---

### Post by P4man on 2010-10-19
By default there wont be a xorg.conf. HOw did you generate or create one?  Proper instructions can be found here, Post #8:

[http://ubuntuforums.org/showthread.php?t=1437980](http://ubuntuforums.org/showthread.php?t=1437980)

This might help too:
[https://wiki.ubuntu.com/X/Config/Resolution](https://wiki.ubuntu.com/X/Config/Resolution)

BTW, you should mention which drivers you are using, proprietary or nouveau?

---

### Post by rockytoprsf on 2010-10-19
First of all, thank you very much for the quick response.

Whatever the display driver is that came with Ubuntu 10.10 is the one I used. I've never had a reason before to have to install a different display driver. [System>Administration>Additional Drivers] indicates that there are no proprietary drivers in use.

To create xorg.conf, I used a different method than that at the link, but the resulting xorg.conf.new should be exactly the same.

From a standing session:

Enter <Ctrl-Alt-F1> to get to CLI login screen.

Login using my ID and password.

Enter "sudo stop gdm" to stop X.

Enter "sudo Xorg -configure" to create xorg.conf.new in my home directory.

Enter "sudo reboot" to reboot the system.

Now, with xorg.conf generated in the xorg.conf.new file, I first tried creating xorg.conf using the 3 sections (Monitor, Device, Screen) from xorg.conf.new that pertain to the display properties. I modified the resulting file by:

- Adding a Modeline line (generated using gtf) to the Monitor section.
- Adding a DefaultDepth line to the Screen section.
- Removing unnecessary Display subsections from the Screen section.
- Adding a Modes line to the remaining Display subsection.

Resulting in the following file for xorg.conf in my home directory:

```
Section "Monitor"
    #DisplaySize      330   250    # mm
    Identifier   "Monitor0"
    VendorName   "CPQ"
    ModelName    "COMPAQ MV720"
    HorizSync    30.0 - 70.0
    VertRefresh  50.0 - 100.0
    Modeline     "1152x864_60.00"  81.62  1152 1216 1336 1520  864 865 868 895  -HSync +Vsync
    Option        "DPMS"
EndSection

Section "Device"
        ### Available Driver options are:-
        ### Values: <i>: integer, <f>: float, <bool>: "True"/"False",
        ### <string>: "String", <freq>: "<f> Hz/kHz/MHz",
        ### <percent>: "<f>%"
        ### [arg]: arg optional
        #Option     "SWcursor"               # [<bool>]
        #Option     "HWcursor"               # [<bool>]
        #Option     "NoAccel"                # [<bool>]
        #Option     "ShadowFB"               # [<bool>]
        #Option     "UseFBDev"               # [<bool>]
        #Option     "Rotate"                 # [<str>]
        #Option     "VideoKey"               # <i>
        #Option     "FlatPanel"              # [<bool>]
        #Option     "FPDither"               # [<bool>]
        #Option     "CrtcNumber"             # <i>
        #Option     "FPScale"                # [<bool>]
        #Option     "FPTweak"                # <i>
        #Option     "DualHead"               # [<bool>]
    Identifier  "Card0"
    Driver      "nv"
    BusID       "PCI:1:0:0"
EndSection

Section "Screen"
    Identifier "Screen0"
    Device     "Card0"
    Monitor    "Monitor0"
    DefaultDepth 16
    SubSection "Display"
        Viewport   0 0
        Depth     16
        Modes     "1152x864"
    EndSubSection
EndSection
```Then, after copying the new xorg.conf from my home directory to /etc/X11 with "sudo cp xorg.conf /etc/X11", I rebooted the PC.

The PC booted to a CLI prompt for login, no GUI desktop.

To get back to a normal desktop, I logged in at the CLI prompt, deleted xorg.conf from /etc/X11, and rebooted.

Next, I tried creating xorg.conf using the 3 sections that I had used previously (Monitor, Device, Screen) with no changes, resulting in the following file:


```
Section "Monitor"
    #DisplaySize      330   250    # mm
    Identifier   "Monitor0"
    VendorName   "CPQ"
    ModelName    "COMPAQ MV720"
    HorizSync    30.0 - 70.0
    VertRefresh  50.0 - 100.0
    Option        "DPMS"
EndSection

Section "Device"
        ### Available Driver options are:-
        ### Values: <i>: integer, <f>: float, <bool>: "True"/"False",
        ### <string>: "String", <freq>: "<f> Hz/kHz/MHz",
        ### <percent>: "<f>%"
        ### [arg]: arg optional
        #Option     "SWcursor"               # [<bool>]
        #Option     "HWcursor"               # [<bool>]
        #Option     "NoAccel"                # [<bool>]
        #Option     "ShadowFB"               # [<bool>]
        #Option     "UseFBDev"               # [<bool>]
        #Option     "Rotate"                 # [<str>]
        #Option     "VideoKey"               # <i>
        #Option     "FlatPanel"              # [<bool>]
        #Option     "FPDither"               # [<bool>]
        #Option     "CrtcNumber"             # <i>
        #Option     "FPScale"                # [<bool>]
        #Option     "FPTweak"                # <i>
        #Option     "DualHead"               # [<bool>]
    Identifier  "Card0"
    Driver      "nv"
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
```Used the same method as before to copy xorg.conf to /etc/X11.

Rebooting gave the same result, boots to CLI prompt to login.

Recovered the same as before by deleting xorg.conf.

Now with 2 failures, I decided to try the complete content of xorg.conf.new unchanged, resulting in the following file:

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
    Load  "extmod"
    Load  "dri2"
    Load  "glx"
    Load  "dri"
    Load  "dbe"
    Load  "record"
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
    #DisplaySize      330   250    # mm
    Identifier   "Monitor0"
    VendorName   "CPQ"
    ModelName    "COMPAQ MV720"
    HorizSync    30.0 - 70.0
    VertRefresh  50.0 - 100.0
    Option        "DPMS"
EndSection

Section "Device"
        ### Available Driver options are:-
        ### Values: <i>: integer, <f>: float, <bool>: "True"/"False",
        ### <string>: "String", <freq>: "<f> Hz/kHz/MHz",
        ### <percent>: "<f>%"
        ### [arg]: arg optional
        #Option     "SWcursor"               # [<bool>]
        #Option     "HWcursor"               # [<bool>]
        #Option     "NoAccel"                # [<bool>]
        #Option     "ShadowFB"               # [<bool>]
        #Option     "UseFBDev"               # [<bool>]
        #Option     "Rotate"                 # [<str>]
        #Option     "VideoKey"               # <i>
        #Option     "FlatPanel"              # [<bool>]
        #Option     "FPDither"               # [<bool>]
        #Option     "CrtcNumber"             # <i>
        #Option     "FPScale"                # [<bool>]
        #Option     "FPTweak"                # <i>
        #Option     "DualHead"               # [<bool>]
    Identifier  "Card0"
    Driver      "nv"
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
```I got exactly the same result.

It boots to a CLI prompt for login, no GUI desktop.

---

### Post by P4man on 2010-10-20
Just FYI; most of xorg.conf can be left empty nowadays. Its just if you want to override the defaults that it needs to be there.

My first thought is... why is it using the nv driver? Your card is supported by nouveau. So try this first; change

```
 Identifier  "Card0"
    Driver      "nv"
    BusID       "PCI:1:0:0"
```


in to

```
 Identifier  "Card0"
    Driver      "nouveau"
    BusID       "PCI:1:0:0"
```

If that doesnt solve it, next things to do is look at (and post) the contents of Xorg.0.log and check the events when X failed to load. Last thought; post the output of xrandr (when you have X running,  at just 1024).

---

### Post by rockytoprsf on 2010-10-20
Success!!!!!!!

OK, Getting the 3 sections (Monitor, Device, Screen) as originally generated by [Xorg -configure], I simply replaced the "nv" with "nouveau" in the Driver statement of the Monitor section, creating the following xorg.conf:

```
Section "Monitor"
    #DisplaySize      330   250    # mm
    Identifier   "Monitor0"
    VendorName   "CPQ"
    ModelName    "COMPAQ MV720"
    HorizSync    30.0 - 70.0
    VertRefresh  50.0 - 100.0
    Option        "DPMS"
EndSection

Section "Device"
        ### Available Driver options are:-
        ### Values: <i>: integer, <f>: float, <bool>: "True"/"False",
        ### <string>: "String", <freq>: "<f> Hz/kHz/MHz",
        ### <percent>: "<f>%"
        ### [arg]: arg optional
        #Option     "SWcursor"               # [<bool>]
        #Option     "HWcursor"               # [<bool>]
        #Option     "NoAccel"                # [<bool>]
        #Option     "ShadowFB"               # [<bool>]
        #Option     "UseFBDev"               # [<bool>]
        #Option     "Rotate"                 # [<str>]
        #Option     "VideoKey"               # <i>
        #Option     "FlatPanel"              # [<bool>]
        #Option     "FPDither"               # [<bool>]
        #Option     "CrtcNumber"             # <i>
        #Option     "FPScale"                # [<bool>]
        #Option     "FPTweak"                # <i>
        #Option     "DualHead"               # [<bool>]
    Identifier  "Card0"
    Driver      "nouveau"
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
```Ubuntu now boots to the expected desktop. Apparently, there is some problem with the way [Xorg -configure] is specifying that Driver statement for my PC.

At this point xrandr generates:

```
Screen 0: minimum 320 x 200, current 1024 x 768, maximum 4096 x 4096
VGA-1 connected 1024x768+0+0 (normal left inverted right x axis y axis) 306mm x 230mm
   1024x768       85.0*    75.1     70.1     60.0  
   800x600        85.1     72.2     75.0     60.3     56.2  
   640x480        85.0     72.8     75.0     60.0  
   720x400        70.1  
   640x350        70.1  
DVI-D-1 disconnected (normal left inverted right x axis y axis)
TV-1 disconnected (normal left inverted right x axis y axis)
```I was able to easily get the resolution (1152 X 864) that I want by making the usual changes to xorg.conf, as I specified in post #3, resulting in the the following xorg.conf:

```
Section "Monitor"
    #DisplaySize      330   250    # mm
    Identifier   "Monitor0"
    VendorName   "CPQ"
    ModelName    "COMPAQ MV720"
    HorizSync    30.0 - 70.0
    VertRefresh  50.0 - 100.0
    Modeline    "1152x864_70.00"  96.77  1152 1224 1344 1536  864 865 868 900  -HSync +Vsync
    Option        "DPMS"
EndSection

Section "Device"
        ### Available Driver options are:-
        ### Values: <i>: integer, <f>: float, <bool>: "True"/"False",
        ### <string>: "String", <freq>: "<f> Hz/kHz/MHz",
        ### <percent>: "<f>%"
        ### [arg]: arg optional
        #Option     "SWcursor"               # [<bool>]
        #Option     "HWcursor"               # [<bool>]
        #Option     "NoAccel"                # [<bool>]
        #Option     "ShadowFB"               # [<bool>]
        #Option     "UseFBDev"               # [<bool>]
        #Option     "Rotate"                 # [<str>]
        #Option     "VideoKey"               # <i>
        #Option     "FlatPanel"              # [<bool>]
        #Option     "FPDither"               # [<bool>]
        #Option     "CrtcNumber"             # <i>
        #Option     "FPScale"                # [<bool>]
        #Option     "FPTweak"                # <i>
        #Option     "DualHead"               # [<bool>]
    Identifier  "Card0"
    Driver      "nouveau"
    BusID       "PCI:1:0:0"
EndSection

Section "Screen"
    Identifier "Screen0"
    Device     "Card0"
    Monitor    "Monitor0"
    DefaultDepth 16
    SubSection "Display"
        Viewport   0 0
        Depth     16
        Modes     "1152x864"
    EndSubSection
EndSection
```Right before I started doing anything today (that's with no xorg.conf in /etc/X11), I did a "dmesg" dump, which showed references to "nouveau", but no references to "nv" (???)

I'm a happy camper now. Thanks for the help.

>>>

[CENTER]*** Update ***
[/CENTER]

After thinking about this for a while, it dawned on me that maybe the default display driver is in fact "nouveau". If that's true, and since I don't make any other changes to the Device section of the 3 sections (Monitor, Device, Screen) that I get to create the new xorg.conf, then I should be able to leave the Device section out completely, only using the other 2 sections (Monitor & Screen) for the new xorg.conf, resulting in:

```
Section "Monitor"
    #DisplaySize      330   250    # mm
    Identifier   "Monitor0"
    VendorName   "CPQ"
    ModelName    "COMPAQ MV720"
    HorizSync    30.0 - 70.0
    VertRefresh  50.0 - 100.0
    Modeline    "1280x1024_60.00"  108.88  1280 1360 1496 1712  1024 1025 1028 1060  -HSync +Vsync
    Option        "DPMS"
EndSection

Section "Screen"
    Identifier "Screen0"
    Monitor    "Monitor0"
    DefaultDepth 16
    SubSection "Display"
        Viewport   0 0
        Depth     16
        Modes     "1280x1024" "1152x864" "1024x768" "800x600"
    EndSubSection
EndSection
```Where:
- Modeline has been changed to 1280x1024 for the highest resolution possible for my card/monitor combination.
- Device section specifier (Device "Card0") has been removed from the Screen section.
- 4 modes are specified (including 1152x864) in the Display subsection of the Screen section.

I thought the 1152x864 resolution would automatically be available, but that didn't happen. So, now adding a Modeline for 1152x864 to the Monitor section, my new xorg.conf is:

```
Section "Monitor"
    #DisplaySize      330   250    # mm
    Identifier   "Monitor0"
    VendorName   "CPQ"
    ModelName    "COMPAQ MV720"
    HorizSync    30.0 - 70.0
    VertRefresh  50.0 - 100.0
    Modeline    "1280x1024_60.00"  108.88  1280 1360 1496 1712  1024 1025 1028 1060  -HSync +Vsync
    Modeline    "1152x864_70.00"  96.77  1152 1224 1344 1536  864 865 868 900  -HSync +Vsync
    Option        "DPMS"
EndSection

Section "Screen"
    Identifier "Screen0"
    Monitor    "Monitor0"
    DefaultDepth 16
    SubSection "Display"
        Viewport   0 0
        Depth     16
        Modes     "1280x1024" "1152x864" "1024x768" "800x600"
    EndSubSection
EndSection
```I now have the 1152x864 resolution back with 1280x1024 available, and I think the xorg.conf is about as simple as it can get to accomplish the desired 1152x864 resolution.

Once again, many thanks to P4man for all the help resolving this problem.

---

