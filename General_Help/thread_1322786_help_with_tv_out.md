---
title: "help with tv out"
date: 2009-11-11
forum: General Help
---

### Post by tim_p on 2009-11-11
hi all Im new here and would like a little help ive been running ubuntu for about a year now and im really happy with it so happy in fact ive built a couple of mediacentre pcs 
both running mythbuntu.
the problem is that on the frontend system which connects to the tv when i reboot im left with a display that is full colour but is two low a resolution so i go into the nvidia settings and change the resolution to the correct one and apply and save to xorg.conf the tv picture is then perfect untill i reboot and then the display is sort of blue/purple if i then restore the backup xorg.conf im back to step 1 with the resolution two low but the colour is perfect ive reinstalled mythbuntu twice to see if i did anything wrong on the install im connecting the the tv using component cables using the nvidia driver here below are the two xorg.confs 
any help would be greatly appreacated thanks
tim
p.s. sorry for such a long post.


xorg.conf this is the purple display but correct resolution

Section "ServerLayout"
    Identifier     "Default Layout"
    Screen      0  "Screen0" 0 0
    InputDevice    "Keyboard0" "CoreKeyboard"
    InputDevice    "Mouse0" "CorePointer"
EndSection

Section "ServerFlags"
    Option         "Xinerama" "0"
EndSection

Section "InputDevice"
    # generated from default
    Identifier     "Keyboard0"
    Driver         "kbd"
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

Section "Monitor"
    Identifier     "Configured Monitor"
EndSection

Section "Monitor"
    Identifier     "Monitor0"
    VendorName     "Unknown"
    ModelName      "TV-0"
    HorizSync       28.0 - 55.0
    VertRefresh     43.0 - 72.0
EndSection

Section "Device"
    Identifier     "Configured Video Device"
    Driver         "nvidia"
    Option         "TVOutFormat" "COMPONENT"
    Option         "NoLogo" "1"
    Option         "UseEvents" "1"
    Option         "ConnectedMonitor" "TV"
    Option         "DPI" "100x100"
    Option         "TVStandard" "HD1080i"
EndSection

Section "Device"
    Identifier     "Device0"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "GeForce 6800"
EndSection

Section "Screen"
    Identifier     "Default Screen"
    Device         "Configured Video Device"
    Monitor        "Configured Monitor"
    DefaultDepth    24
EndSection

Section "Screen"
    Identifier     "Screen0"
    Device         "Device0"
    Monitor        "Monitor0"
    DefaultDepth    24
    Option         "TwinView" "0"
    Option         "metamodes" "1920x1080 +0+0"
    SubSection     "Display"
        Depth       24
    EndSubSection
EndSection


and here is the correct colour but thedisplay is two low a resolution

Section "Monitor"
    Identifier    "Configured Monitor"
EndSection

Section "Screen"
    Identifier    "Default Screen"
    Monitor        "Configured Monitor"
    Device        "Configured Video Device"
    DefaultDepth    24
EndSection

Section "Device"
    Identifier    "Configured Video Device"
    Driver    "nvidia"
    Option    "TVOutFormat"    "COMPONENT"
    Option    "NoLogo"    "1"
    Option    "UseEvents"    "1"
    Option    "ConnectedMonitor"    "TV"
    Option    "DPI"    "100x100"
    Option    "TVStandard"    "HD1080i"
EndSection

---

