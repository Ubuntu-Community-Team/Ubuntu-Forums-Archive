---
title: "My first plunge into Ubuntu"
date: 2010-04-06
forum: General Help
---

### Post by Comokanu on 2010-04-06
I've a laptop from 2001 with 512MB of RAM, and I was running Windows XP, and the laptop wasn't coping very well with the huge demands of the applications of today. It was only yesterday I installed Ubuntu alongside XP and I was surprised to see how fast everything was!

The only thing that's bugging me a bit is the screen. Some parts of the desktop shows some banding where there is meant to be a gradient, probably telling me to increase the color depth. Is there a way in Karmic Koala to change the color depth? I tried using **sudo gedit /etc/X11/xorg.conf** but when the editor shows up with the setting file, it's empty.
 
Thank you in advance

---

### Post by mickObrian on 2010-04-06
I don't think you installed the driver and/or you didn't configure it, what type of graphics card do you have?

---

### Post by Yvan300 on 2010-04-06
> **mickObrian said:**
> I don't think you installed the driver and/or you didn't configure it, what type of graphics card do you have?

Such an old laptop would most likely have a 'legacy' graphics card. So he would have to use the open source drivers. But then again, i can be wrong. But anyways the poster needs to explain himself a little better. Are you trying to say that the edges of the screen a different color or something?

---

### Post by quadproc on 2010-04-06
> **Comokanu said:**
> ...
The only thing that's bugging me a bit is the screen. Some parts of the desktop shows some banding where there is meant to be a gradient, probably telling me to increase the color depth. Is there a way in Karmic Koala to change the color depth? I tried using **sudo gedit /etc/X11/xorg.conf** but when the editor shows up with the setting file, it's empty.
 

As I understand it, xorg.conf is optional in 9.10; if you don't have one then the software will examine the hardware and try to do what makes sense.  But if you do have an xorg.conf then it should use that.  If you have an old xorg.conf file from a previous release then you might use that as a starting point.  If you place the file in /etc/X11 and restart the X server then it should pay attention to your file.

quadproc

---

### Post by Comokanu on 2010-04-07
I've got a nVidia graphics-n 16MB. And about the xorg.conf, do you have any templates that I can paste and work around? 

I checked the color depth on Terminal and it showed 24-bits, which was very unlikely looking at the color banding on the screen.

---

### Post by rossmoore on 2010-04-07
can you take a screenshot for us?

---

### Post by Comokanu on 2010-04-07
Of course, I'm so sorry :L If you look REALLY carefully at full zoom

---

### Post by rossmoore on 2010-04-07
The background looks good, but the gnome-panel (that's the top and bottom bars that you've got in graded black/grey) looks a bit dodgy. Is it that that you're referring to?

---

### Post by Comokanu on 2010-04-07
I'm sorry, that's just the theme that's all. Look really close at the background where the blue fades into navy.

---

### Post by quadproc on 2010-04-07
> **Comokanu said:**
> I've got a nVidia graphics-n 16MB. And about the xorg.conf, do you have any templates that I can paste and work around? 

Sure; the listing below is what I am running but with the comments removed.  Please note that I have ATI HD4870x2 and I am using the fglrx driver; you'll need to change those things for sure.
```


Section "ServerLayout"
    Identifier     "aticonfig Layout"
    Screen      0  "aticonfig-Screen[0]-0" 0 0
EndSection

Section "Files"
EndSection

Section "Module"
EndSection

Section "ServerFlags"
    Option        "DontZap" "False"
EndSection

Section "Monitor"
# I added the following line on 1/19/10
    Identifier   "Configured Monitor"
    Option        "DPMS"
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
    BusID       "PCI:2:0:0"
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

```I believe that "dontzap" is now obsolete but it doesn't seem to hurt anything so I left it in.

The first "monitor" section is now redundant but it doesn't seem to be causing trouble so I have not removed it.

The BusID will almost certainly be different for your system - that is the bus address of the primary graphics card.  That address is a function of the design of the mother board and of which slots the graphics cards occupy.  In my case, it was a necessity to specify this as the X server could not figure out which graphics card was the primary device so it just gave up and quit executing without even creating a log.  Adding the BusID was a workaround for this problem.

A lot of the empty sections were installed by ATI's driver installation software.  I don't know why it put in those empty sections but I figured that I would leave them alone as long as things were working OK.

quadproc

---

### Post by rossmoore on 2010-04-07
```
# nvidia-xconfig: X configuration file generated by nvidia-xconfig
# nvidia-xconfig:  version 1.0  (buildmeister@builder75)  Tue Dec  8 21:04:28 PST 2009

# nvidia-settings: X configuration file generated by nvidia-settings
# nvidia-settings:  version 1.0  (buildd@leucaena)  Wed Dec 23 23:29:52 UTC 2009

Section "ServerLayout"
    Identifier     "Layout0"
    Screen      0  "Screen0" 0 0
    InputDevice    "Keyboard0" "CoreKeyboard"
    InputDevice    "Mouse0" "CorePointer"
    Option         "Xinerama" "0"
EndSection

Section "Files"
EndSection

Section "InputDevice"

    # generated from default
    Identifier     "Mouse0"
    Driver         "mouse"
    Option         "Protocol" "auto"
    Option         "Device" "/dev/psaux"
    Option         "Emulate3Buttons" "no"
    Option         "ZAxisMapping" "4 5"
EndSection

Section "InputDevice"

    # generated from default
    Identifier     "Keyboard0"
    Driver         "kbd"
EndSection

Section "Monitor"

    # HorizSync source: edid, VertRefresh source: edid
    Identifier     "Monitor0"
    VendorName     "Unknown"
    ModelName      "LG TV"
    HorizSync       28.0 - 67.0
    VertRefresh     50.0 - 75.0
    Option         "DPMS"
EndSection

Section "Device"
    Identifier     "Device0"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "ION"
EndSection

Section "Screen"
    Identifier     "Screen0"
    Device         "Device0"
    Monitor        "Monitor0"
    DefaultDepth    24
    Option         "TwinView" "0"
    Option         "metamodes" "1360x768_60 +0+0"
    SubSection     "Display"
        Depth       24
    EndSubSection
EndSection

Section "Extensions"
    Option         "Composite" "Disable"
EndSection

```

Here is my xorg.conf, from a much newer nvidia setup than yours. The composite disable bit at the end is to get around a vblank issue with videos in vdpau.

---

