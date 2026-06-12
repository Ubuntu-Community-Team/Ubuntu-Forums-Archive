---
title: "Have to restart gdm after boot to get third monitor working"
date: 2010-05-02
forum: General Help
---

### Post by KrisWillis on 2010-05-02
Hi there,

I have a three monitor set-up under 9.10, the monitors are connected to a pair of nvida 512MB GT240s, two on one, one on the other. After booting, I get the logon screen but only two of my monitors have a picture; to get the third running I need to login and restart gdm within a terminal and then login again.

I'm using the proprietary nvidia 185.18.36 drivers (which oddly report my cards as 1024MB GT230s), with Xinerama. My xorg is included below, if that helps.

Does anyone have any ideas as to how I can fix this?


```
Section "ServerLayout"
    Identifier     "Layout0"
    Screen      0  "Screen0" RightOf "Screen1"
    Screen      1  "Screen1" 1920 0
    Screen      2  "Screen2" LeftOf "Screen1"
    InputDevice    "Keyboard0" "CoreKeyboard"
    InputDevice    "Mouse0" "CorePointer"
EndSection

Section "Module"
    Load           "dbe"
    Load           "extmod"
    Load           "type1"
    Load           "freetype"
    Disable	   "glx"
EndSection

Section "ServerFlags"
    Option         "Xinerama" "on"
EndSection

Section "InputDevice"
    Identifier     "Keyboard0"
    Driver         "keyboard"
EndSection

Section "InputDevice"
    Identifier     "Mouse0"
    Driver         "mouse"
    Option         "Protocol" "auto"
    Option         "Device" "/dev/psaux"
    Option         "Emulate3Buttons" "no"
    Option         "ZAxisMapping" "4 5"
EndSection

Section "Monitor"
    Identifier     "Monitor0"
EndSection

Section "Monitor"
    Identifier     "Monitor1"
EndSection

Section "Monitor"
    Identifier     "Monitor2"
EndSection

Section "Device"
    Identifier     "Videocard0"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "GeForce GT240"
    BusID          "PCI:03:00:0"
EndSection

Section "Device"
    Identifier     "Videocard1"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "GeForce GT240"
    BusID          "PCI:05:00:0"
    Screen          0
EndSection

Section "Device"
    Identifier     "Videocard2"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "GeForce GT240"
    BusID          "PCI:05:00:0"
    Screen          1
EndSection

Section "Screen"
    Identifier     "Screen0"
    Device         "Videocard0"
    Monitor        "Monitor0"
    DefaultDepth    24
    Option         "metamodes" "1920x1080 +0+0"
    Option         "RenderAccel" "1"
    Option         "CursorShadow" "1"
    Option         "Coolbits" "1"
    Option         "NoPowerConnectorCheck"
    Option         "VideoOverlay" "on"
    Option         "OpenGLOverlay" "off"
    Option         "NoLogo" "True"
    SubSection     "Display"
        Depth       24
        Modes      "1920x1080"
    EndSubSection
EndSection

Section "Screen"
    Identifier     "Screen1"
    Device         "Videocard1"
    Monitor        "Monitor1"
    DefaultDepth    24
    Option         "metamodes" "1920x1080 +0+0"
    Option         "RenderAccel" "1"
    Option         "CursorShadow" "1"
    Option         "Coolbits" "1"
    Option         "NoPowerConnectorCheck"
    Option         "VideoOverlay" "on"
    Option         "OpenGLOverlay" "off"
    Option         "NoLogo" "True"
    SubSection     "Display"
        Depth       24
        Modes      "1920x1080"
    EndSubSection
EndSection

Section "Screen"
    Identifier     "Screen2"
    Device         "Videocard2"
    Monitor        "Monitor2"
    DefaultDepth    24
    Option         "metamodes" "1920x1080 +0+0"
    Option         "RenderAccel" "1"
    Option         "CursorShadow" "1"
    Option         "Coolbits" "1"
    Option         "NoPowerConnectorCheck"
    Option         "VideoOverlay" "on"
    Option         "OpenGLOverlay" "off"
    Option         "NoLogo" "True"
    SubSection     "Display"
        Depth       24
        Modes      "1920x1080"
    EndSubSection
EndSection

Section "Extensions"
    Option         "Composite" "false"
EndSection

```

---

### Post by KrisWillis on 2010-05-05
Bump

---

### Post by dino99 on 2010-05-05
in case: sudo dpkg-reconfigure gdm

but you might watch .xsession-errors and xorg.0.log for more details (system-admin-log viewer)

are you using nvidia-settings and compare your xorg.conf with its settings ?

you have: videocard0, 1, 2,
i'm not sure about that but in fact you only have videocard0 and 1, so maybe some confusion here, might check without videocard2 as 1&2 is the same card.

---

