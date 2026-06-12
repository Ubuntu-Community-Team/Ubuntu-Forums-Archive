---
title: "Can not log in after 11.04 update"
date: 2011-05-02
forum: General Help
---

### Post by gatordude on 2011-05-02
I did the update and all went well. I could reboot and log back in with no issues. I was trying to get my dual monitors setup how I had them before and when I made a change for multiple desktops (ATI Catalyst Center) I rebooted and now pc comes up to the log in screen (single user , single OS) I type my password and it tries to come up for a few seconds and then goes back to the log in screen.
I am currently using a 9.1 live cd so I know my hardware is fine.

Any ideas?

---

### Post by gatordude on 2011-05-02
OK I cleared out xorg and rebooted and then logged in.
Started making my changes: First one was single monitor multiple desktops and then I rebooted. No Problems. Second was Xinema (to drag windows across from one to the next) rebooted and I could not log back in?
```
 Section "ServerLayout"
    Identifier     "amdcccle Layout"
    Screen      0  "amdcccle-Screen[1]-0" 1680 0
    Screen         "amdcccle-Screen[1]-1" 0 0
EndSection

Section "ServerFlags"
    Option        "Xinerama" "on"
EndSection

Section "Monitor"
    Identifier   "Configured Monitor"
EndSection

Section "Monitor"
    Identifier   "0-CRT1"
    Option        "VendorName" "ATI Proprietary Driver"
    Option        "ModelName" "Generic Autodetecting Monitor"
    Option        "DPMS" "true"
    Option        "PreferredMode" "1680x1050"
    Option        "TargetRefresh" "60"
    Option        "Position" "0 0"
    Option        "Rotate" "normal"
    Option        "Disable" "false"
EndSection

Section "Monitor"
    Identifier   "0-DFP1"
    Option        "VendorName" "ATI Proprietary Driver"
    Option        "ModelName" "Generic Autodetecting Monitor"
    Option        "DPMS" "true"
    Option        "PreferredMode" "1680x1050"
    Option        "TargetRefresh" "60"
    Option        "Position" "0 0"
    Option        "Rotate" "normal"
    Option        "Disable" "false"
EndSection

Section "Device"
    Identifier  "Configured Video Device"
EndSection

Section "Device"
    Identifier  "amdcccle-Device[1]-0"
    Driver      "fglrx"
    Option        "Monitor-DFP1" "0-DFP1"
    BusID       "PCI:1:5:0"
EndSection

Section "Device"
    Identifier  "amdcccle-Device[1]-1"
    Driver      "fglrx"
    Option        "Monitor-CRT1" "0-CRT1"
    BusID       "PCI:1:5:0"
    Screen      1
EndSection

Section "Screen"
    Identifier "Default Screen"
    Device     "Configured Video Device"
    Monitor    "Configured Monitor"
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

```

Any ideas why I cant log in with Xinema ticked?

---

### Post by kutar0720 on 2011-06-02
I have the same problem with you. I'm stuck in the gnome log in screen after ticking the xinema option.
By the way, in which directory can I find the xorg config file to reset it?

---

