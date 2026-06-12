---
title: "carte ATI RADEON 3850 / Screen divided in two horizontally"
date: 2012-01-30
forum: General Help
---

### Post by quoidautre on 2012-01-30
Hi all,

 I have a huge oddity in my version 11.10. I re-installed the driver for my ATI Radeon HD 3850. And now, my screen is divided horizontally into two :(

 Here is the screenshot [here]("http://hpics.li/85aada1") : [[img]http://img11.hostingpics.net/pics/728980capture.jpg[/img]](http://www.hostingpics.net/viewer.php?id=728980capture.jpg)
[IMG]http://hpics.li/85aada1[/IMG]
 and the xorg.conf: ```
Section "ServerLayout"
    Identifier     "aticonfig Layout"
    Screen      0  "aticonfig-Screen[0]-0" 0 0
EndSection

Section "Module"
    Load  "glx"
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
    Identifier "Default Screen"
    DefaultDepth     24
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

``` Otherwise, I did that too:

 - Sudo apt-get remove fglrx *

 - Sudo sh *- ./ati-driver-installer- x86.x86_64.run - buildandinstallpkg

 I had an error on this:

 - Sudo dpkg-i *. deb

 Then I did this:

 - Sudo / usr / bin / aticonfig - initial

 Reboot, and it makes no difference. 

Any idea ?

 Fabrice

---

