---
title: "xorg.conf and Unity3D"
date: 2012-05-05
forum: General Help
---

### Post by oshirowanen on 2012-05-05
Is it possible to change my xorg.conf so I can use Unity3D?

    Section "ServerLayout"
        Identifier     "Layout0"
        Screen      0  "Screen0" 0 0
        Screen      1  "Screen1" RightOf "Screen0"
        Screen      2  "Screen2" RightOf "Screen1"
        Screen      3  "Screen3" RightOf "Screen2"
        InputDevice    "Keyboard0" "CoreKeyboard"
        InputDevice    "Mouse0" "CorePointer"
        Option         "Xinerama" "1"
    EndSection
    
    Section "Files"
    EndSection
    
    Section "InputDevice"
        Identifier     "Mouse0"
        Driver         "mouse"
        Option         "Protocol" "auto"
        Option         "Device" "/dev/psaux"
        Option         "Emulate3Buttons" "no"
        Option         "ZAxisMapping" "4 5"
    EndSection
    
    Section "InputDevice"
        Identifier     "Keyboard0"
        Driver         "kbd"
    EndSection
    
    Section "Monitor"
        Identifier     "Monitor0"
        VendorName     "Unknown"
        ModelName      "Acer AL1916"
        HorizSync       31.0 - 83.0
        VertRefresh     56.0 - 75.0
        Option         "DPMS"
    EndSection
    
    Section "Monitor"
        Identifier     "Monitor1"
        VendorName     "Unknown"
        ModelName      "Acer AL1916"
        HorizSync       31.0 - 83.0
        VertRefresh     56.0 - 75.0
        Option         "DPMS"
    EndSection
    
    Section "Monitor"
        Identifier     "Monitor2"
        VendorName     "Unknown"
        ModelName      "Acer AL1916"
        HorizSync       31.0 - 83.0
        VertRefresh     56.0 - 75.0
        Option         "DPMS"
    EndSection
    
    Section "Monitor"
        Identifier     "Monitor3"
        VendorName     "Unknown"
        ModelName      "Acer AL1916"
        HorizSync       31.0 - 83.0
        VertRefresh     56.0 - 75.0
        Option         "DPMS"
    EndSection
    
    Section "Device"
        Identifier     "Device0"
        Driver         "nvidia"
        VendorName     "NVIDIA Corporation"
        BoardName      "GeForce GT 520"
        BusID          "PCI:1:0:0"
        Screen          0
    EndSection
    
    Section "Device"
        Identifier     "Device1"
        Driver         "nvidia"
        VendorName     "NVIDIA Corporation"
        BoardName      "GeForce GT 520"
        BusID          "PCI:1:0:0"
        Screen          1
    EndSection
    
    Section "Device"
        Identifier     "Device2"
        Driver         "nvidia"
        VendorName     "NVIDIA Corporation"
        BoardName      "GeForce GT 520"
        BusID          "PCI:6:0:0"
        Screen          0
    EndSection
    
    Section "Device"
        Identifier     "Device3"
        Driver         "nvidia"
        VendorName     "NVIDIA Corporation"
        BoardName      "GeForce GT 520"
        BusID          "PCI:6:0:0"
        Screen          1
    EndSection
    
    Section "Screen"
        Identifier     "Screen0"
        Device         "Device0"
        Monitor        "Monitor0"
        DefaultDepth    24
        Option         "TwinView" "0"
        Option         "TwinViewXineramaInfoOrder" "CRT-0"
        Option         "metamodes" "CRT-0: 1280x1024_75 +0+0"
        SubSection     "Display"
            Depth       24
        EndSubSection
    EndSection
    
    Section "Screen"
        Identifier     "Screen1"
        Device         "Device1"
        Monitor        "Monitor1"
        DefaultDepth    24
        Option         "TwinView" "0"
        Option         "metamodes" "CRT-1: 1280x1024_75 +0+0"
        SubSection     "Display"
            Depth       24
        EndSubSection
    EndSection
    
    Section "Screen"
        Identifier     "Screen2"
        Device         "Device2"
        Monitor        "Monitor2"
        DefaultDepth    24
        Option         "TwinView" "0"
        Option         "metamodes" "CRT-0: 1280x1024_75 +0+0"
        SubSection     "Display"
            Depth       24
        EndSubSection
    EndSection
    
    Section "Screen"
        Identifier     "Screen3"
        Device         "Device3"
        Monitor        "Monitor3"
        DefaultDepth    24
        Option         "TwinView" "0"
        Option         "metamodes" "CRT-1: 1280x1024_75 +0+0"
        SubSection     "Display"
            Depth       24
        EndSubSection
    EndSection

At the moment, if I chose Unity3D, it will just display on 1 screen, if I choose Unity2D it will mirror 1 screen to all screens, so I have to resort to gnome-classic to get all 4 screens to work with the above xorg.conf.

---

