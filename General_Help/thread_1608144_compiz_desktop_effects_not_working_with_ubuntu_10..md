---
title: "compiz desktop effects not working with ubuntu 10.04 and ati card"
date: 2010-10-28
forum: General Help
---

### Post by mattybadger on 2010-10-28
Hi all, I have been searching various forums  for a couple of evenings so I am aware there have been numerous threads with very similar problems so apologies. Unfortunately none of the suggestions I have seen in these threads have helped me solve them. I had tried a few things from downloading the open source ati drivers to making a couple of minor amendments to the xorg.conf

The original problem I had was when I had desktop effects enabled (I had it working for a short while) there was a couple of second delay when opening, minimizing or resizing a window. I went to ATI's site and downloaded the latest drivers from there. Since then I have not been able to get any desktop effects and receive the 'desktop effects could not be enabled' message. Strangely enough despite desktop effects working before I still had the same message when I ran the check compiz command in the terminal.  

If anyone has any suggestions they would be most welcome. 

Card details

```
badger@badger-laptop:~$ lspci | grep VGA
01:00.0 VGA compatible controller: ATI Technologies Inc Mobility Radeon HD 3650
```Check compiz info

```
Gathering information about your system...

 Distribution:          Ubuntu 10.04
 Desktop environment:   GNOME
 Graphics chip:         ATI Technologies Inc Mobility Radeon HD 3650
 Driver in use:         fglrx
 Rendering method:      None

Checking if it's possible to run Compiz on your system...  [SKIP]

 Checking for hardware/setup problems...           [SKIP]

At least one check had to be skipped:
 Error: No rendering method in use (AIGLX, Xgl or Nvidia)

```

xorg.conf

```
Section "ServerLayout"
    Identifier     "amdcccle Layout"
    Screen      0  "amdcccle-Screen[1]-0" 0 0
    Screen         "amdcccle-Screen[1]-1" RightOf "amdcccle-Screen[1]-0"
    Option "AIGLX" "on"
EndSection

Section "Files"
EndSection

Section "Module"
    Load  "glx"
EndSection

Section "Monitor"
    Identifier   "0-CRT1"
    Option        "VendorName" "ATI Proprietary Driver"
    Option        "ModelName" "Generic Autodetecting Monitor"
    Option        "DPMS" "true"
    Option        "Disable" "false"
    Option        "PreferredMode" "1440x900"
    Option        "TargetRefresh" "60"
    Option        "Position" "0 0"
    Option        "Rotate" "normal"
EndSection

Section "Monitor"
    Identifier   "0-LVDS"
    Option        "VendorName" "ATI Proprietary Driver"
    Option        "ModelName" "Generic Autodetecting Monitor"
    Option        "DPMS" "true"
    Option        "PreferredMode" "1440x900"
    Option        "TargetRefresh" "61"
    Option        "Position" "0 0"
    Option        "Rotate" "normal"
    Option        "Disable" "false"
EndSection

Section "Device"
    Identifier  "Default Device"
    Driver      "fglrx"
    BusID       "PCI:1:0:0"
    Option "TexturedXrender" "on"
    Option "UseFastTLS" "1" 
    Option "BackingStore" "on" 
EndSection

Section "Device"
    Identifier  "amdcccle-Device[1]-0"
    Driver      "fglrx"
    Option        "Monitor-LVDS" "0-LVDS"
    Option        "Monitor-CRT1" "0-CRT1"
    BusID       "PCI:1:0:0"
    Option "TexturedXrender" "on"
    Option "UseFastTLS" "1" 
    Option "BackingStore" "on"
EndSection

Section "Device"
    Identifier  "amdcccle-Device[1]-1"
    Driver      "fglrx"
    Option        "Monitor-LVDS" "0-LVDS"
    BusID       "PCI:1:0:0"
    Screen      1
EndSection

Section "Screen"
    Identifier "Default Screen"
    DefaultDepth     24
EndSection

Section "Screen"
    Identifier "amdcccle-Screen[1]-0"
    Device     "amdcccle-Device[1]-0"
    DefaultDepth     24
    SubSection "Display"
        Viewport   0 0
        Depth     24
    EndSubSection
EndSection

Section "Screen"
    Identifier "amdcccle-Screen[1]-1"
    Device     "amdcccle-Device[1]-1"
    DefaultDepth     24
    SubSection "Display"
        Viewport   0 0
        Depth     24
    EndSubSection
EndSection

```I can't paste what is returned from the normal compiz command as I get error messages in the terminal, then my laptop's keyboard will stop working until I restart.

---

### Post by dcstar on 2010-10-29
> **mattybadger said:**
> Hi all, I have been searching various forums  for a couple of evenings so I am aware there have been numerous threads with very similar problems so apologies. Unfortunately none of the suggestions I have seen in these threads have helped me solve them. I had tried a few things from downloading the open source ati drivers to making a couple of minor amendments to the xorg.conf

The original problem I had was when I had desktop effects enabled (I had it working for a short while) there was a couple of second delay when opening, minimizing or resizing a window. **I went to ATI's site and downloaded the latest drivers from there. Since then I have not been able to get any desktop effects **and receive the 'desktop effects could not be enabled' message. Strangely enough despite desktop effects working before I still had the same message when I ran the check compiz command in the terminal.  
........

Reinstall the Ubuntu supplied drivers.

---

### Post by philak on 2010-11-13
I did a fresh install 10.04. compiz was very unstable. I found an answer to my problem here,( [http://forum.compiz.org/viewtopic.php?f=86&t=12552&start=20](http://forum.compiz.org/viewtopic.php?f=86&t=12552&start=20) ) about disabling KMS. Hope this helps. This is an older Emachine with radeon express 200 graphics.

---

### Post by cpmman on 2010-11-13
I had a compiz problem and followed this advice which corrected it:-

[***_http://ubuntuforums.org/showpost.php?p=9964610&postcount=2_***]("http://ubuntuforums.org/showpost.php?p=9964610&postcount=2")

---

