---
title: "fglrx and font scaling"
date: 2009-06-25
forum: General Help
---

### Post by newio on 2009-06-25
Hi All,

I've just setup a big desktop using aticonfig:

aticonfig --initial
aticonfig --dtop=horizontal --overlay-on=1

The desktop stretched across my two screens fine (1600x1050 1600x1050). But thee font scaling was all messed up! the font where tiny and barely readable. I've managed to get a "sort of" useful install happening by:
  1. Setting font sizes as 18 in KDE System Settings
  2. doing to about:config in firefox and setting the layout:DPI to 75

However, applications are failing to honor these font settings. I really dont want to setup custom fonts for every application i use. In the attached screenshots, Kopete is showing massive fonts, OpenOffice is showing correctly sized font (albeit, its using Font size 12, which is the same size as the desktop fonts which are set to 18).

Has anyone else come across this? Its really annoying having every app displayed differently. Also, the login screen still has tiny fonts.

Any help appreciated


xorg.conf
```

Section "ServerLayout"
        Identifier     "aticonfig Layout"
        Screen      0  "aticonfig-Screen[0]-0" 0 0
EndSection

Section "Files"
EndSection

Section "Module"
EndSection

Section "Monitor"
        Identifier   "aticonfig-Monitor[0]-0"
        Option      "VendorName" "ATI Proprietary Driver"
        Option      "ModelName" "Generic Autodetecting Monitor"
        Option      "DPMS" "true"
EndSection

Section "Device"
        Identifier  "aticonfig-Device[0]-0"
        Driver      "fglrx"
        Option      "DesktopSetup" "horizontal"
        Option      "VideoOverlay" "on"
        Option      "OpenGLOverlay" "off"
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

```
[IMG]http://img37.imageshack.us/img37/6123/fontsv.png[/IMG]

---

### Post by newio on 2009-06-25
problem solved...

The DisplaySize in my xorg.conf was not set correctly. To get the correct setting, i needed to use this:

(dimension x 24.4 / desired DPI)

1600 x 24.4 / 100 = 406
1050 x 24.4 / 100 = 267

and in the Monitor Section of xorg.conf set:
DisplaySize 406 267

...still pretty annoying this wasn't set my default by X or aticonfig...

---

