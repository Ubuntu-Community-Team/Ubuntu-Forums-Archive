---
title: "Xubuntu Dual Monitor, two graphics cards, Xinerama crash"
date: 2009-06-30
forum: General Help
---

### Post by rowlandm on 2009-06-30
Hi there,

I have been trying to get Xinerama to work with my machine:

[LIST]
[*]Intel Corporation 82845G/GL[Brookdale-G]/GE Chipset Integrated Graphics Device (rev 01) for one monitor
[*]Nvidia graphics card GeForce4 MX 4000 PCI for the other monitor
[*]identical monitors
[*]Xfce Xubuntu
[/LIST]

My current xorg works with Xinerama off.  I get dual screens and I cannot move windows between them.  As soon as I remove the comment to turn Xinerama on, my X breaks with the error:

> GLX load failure on nvidia  
well I used to get it - now I consistently get
> (EE) intel(0): [dri] I830CheckDRIAvailable failed: glx not loaded



My current xorg looks like this

> Section "ServerLayout"
    Identifier     "X.org Configured"
    Screen      0  "Screen0" 0 0
    Screen      1  "Screen1" RightOf "Screen0"
    InputDevice    "Mouse0" "CorePointer"
    InputDevice    "Keyboard0" "CoreKeyboard"
#    Option "Xinerama" "on"
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
    #DisplaySize 400 250 # mm
    Identifier "Monitor0"
    VendorName "AOC"
    ModelName "917W"
    ### Comment all HorizSync and VertRefresh values to use DDC:
    Option "DPMS"
EndSection

Section "Monitor"
    #DisplaySize 400 250 # mm
    Identifier "Monitor1"
    VendorName "AOC"
    ModelName "917W"
    ### Comment all HorizSync and VertRefresh values to use DDC:
    Option "DPMS"
EndSection

Section "Device"
        ### Available Driver options are:-
        ### Values: <i>: integer, <f>: float, <bool>: "True"/"False",
        ### <string>: "String", <freq>: "<f> Hz/kHz/MHz"
        ### [arg]: arg optional
        #Option     "ShadowFB"               # [<bool>]
        #Option     "DefaultRefresh"         # [<bool>]
        #Option     "ModeSetClearScreen"     # [<bool>]
    Identifier  "Card0"
    Driver      "intel"
    VendorName  "Intel Corporation"
    BoardName   "82845G/GL[Brookdale-G]/GE Chipset Integrated Graphics Device"
    BusID       "PCI:0:2:0"
EndSection

Section "Device"
        ### Available Driver options are:-
        ### Values: <i>: integer, <f>: float, <bool>: "True"/"False",
        ### <string>: "String", <freq>: "<f> Hz/kHz/MHz"
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
    Identifier  "Card1"
    Driver      "nvidia"
    VendorName  "nVidia Corporation"
    BoardName   "NV18 [GeForce4 MX 4000 AGP 8x]"
    BusID       "PCI:5:4:0"
    #Option     "Twinview"     "True"
    #Option    "TwinViewOrientation"     "RightOf"
    #Option    "UseEdidFreqs"     "True"
    #Option    "MetaModes"    "1024x768,1024x768"
    #Option    "UseDisplayDevice"    "CRT"
EndSection

Section "Screen"
    Identifier "Screen0"
    Device "Card0"
    Monitor "Monitor0"
    DefaultDepth 24    
    Subsection "Display"
        Depth 24 
        #Modes "1024x768"
        Modes "1280x1024"
    EndSubsection
EndSection

Section "Screen"
    Identifier "Screen1"
    Device "Card1"
    Monitor "Monitor1"
    DefaultDepth 24    
    Subsection "Display"
        Depth 24
        Modes "1280x1024"
        #Modes "1024x768"
    EndSubsection
EndSection



and I currently get these errors in my xorg.0.log (with Xinerama turned off)

> (EE) intel(0): [dri] I830CheckDRIAvailable failed: glx not loaded
(EE) intel(0): Failed to pin xv buffeOther points to note:
[LIST]
[*]I can get Xinerama working with another Linux OS slitaz
[*]The slitaz Xorg was used as a base for this xorg
[*]I am assuming Twinview only works for nvidia card with two heads, not across another non-nvidia video card
[*]Someone mentioned to disable glx specifically, but that didn't seem to work, but I might have done it incorrectly
[*]This is in Jaunty 9.04, tried it in 8.04 LTS but had similar results
[*]I have a nagging feeling that the nvidia driver that was installed before is not really being used at the moment.  The hard ware drivers seem to say it is not activated.....
[*]When I try and get into the Settings -> display or Nvidia X Settings program it logs me out and I go back to a default login page.
[/LIST]

Can anyone let me know if they have been able to get this working, or what I can try from here on in, or if this is even possible?  I have other options I know but I wanted to get Xinerama working if I could. Thanks in advance

---

