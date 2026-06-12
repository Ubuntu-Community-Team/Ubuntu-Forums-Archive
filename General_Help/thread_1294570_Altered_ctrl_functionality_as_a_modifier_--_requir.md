---
title: "Altered ctrl functionality as a modifier -- requires shift+ctrl"
date: 2009-10-18
forum: General Help
---

### Post by falconindy on 2009-10-18
I'm no longer able to use solely Ctrl to perform the functionality it once did, i.e. selecting multiple files in Nautilus, or opening a link in a new tab in Chromium. These actions now require shift as well.

I'm fairly sure this coincided with when I upgraded my nvidia drivers to version 185, and moreover, tied in to xorg.conf. However, I can't spot the change in the two xorg config files. Here's my current xorg.conf:
```
Section "ServerLayout"
    Identifier     "Default Layout"
    Screen         "Default Screen" 0 0
    InputDevice    "Keyboard0" "CoreKeyboard"
    InputDevice    "Mouse0" "CorePointer"
EndSection

Section "Module"
    Load           "glx"
EndSection

Section "InputDevice"
    # generated from default
    Identifier     "Keyboard0"
    Driver         "keyboard"
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

Section "Device"
    Identifier     "Configured Video Device"
    Driver         "nvidia"
EndSection

Section "Screen"
    Identifier     "Default Screen"
    Device         "Configured Video Device"
    Monitor        "Configured Monitor"
    DefaultDepth    24
    Option         "NoLogo" "True"
    SubSection     "Display"
        Depth       24
        Modes      "nvidia-auto-select"
    EndSubSection
EndSection
```
Anyone else experienced this? Or better yet, know what I've missed?

---

