---
title: "VIA Driver"
date: 2010-09-11
forum: General Help
---

### Post by Mirgeee on 2010-09-11
Hi there,
I've succeeded in installing VIA Driver on my Lenovo S12 Nano, VX800, it's been sort of struggle, I have to say.
I finally configured teh xorg file the way it works, without XRandr though. After reboot, the screen is kinda blinking, the cursor is moving rather hitchily and overall performance is worse to me (maybe set higher fps?). Nevertheless, I got Gimp and wine working, which is what I was looking for.
Here's my xorg. Don't you know how to enable XRandr or solve the issues above?
Thanks a lot
Mirgeee
```
Section "ServerLayout"
    Identifier     "X.org Configured"
    Screen      0  "Screen0" 0 0
    Option            "RandR" "False"
    InputDevice    "Mouse0" "CorePointer"
    InputDevice    "Keyboard0" "CoreKeyboard"
EndSection

Section "Files"
    RgbPath      "/etc/X11/rgb"
    ModulePath   "/usr/lib/xorg/modules"
    FontPath     "/usr/share/fonts/X11/misc"
    FontPath     "/usr/share/fonts/X11/cyrillic"
    FontPath     "/usr/share/fonts/X11/100dpi/:unscaled"
    FontPath     "/usr/share/fonts/X11/75dpi/:unscaled"
    FontPath     "/usr/share/fonts/X11/Type1"
    FontPath     "/usr/share/fonts/X11/100dpi"
    FontPath     "/usr/share/fonts/X11/75dpi"
    FontPath     "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
EndSection

Section "Module"
    Load  "xtrap"
    Load  "dri"
    Load  "glx"
    Load  "record"
    Load  "dbe"
    Load  "GLcore"
    Load  "extmod"
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


Section "Device"
    Identifier  "Card0"
    Driver      "via"
    VendorName  "VIA Tech"
    BoardName   "VIA Chrome9 HC3"
    Option        "AccelMethod"    "EXA"
    BusID       "PCI:0:1:0"
    Option        "ActiveDevice" "LCD"
    Option         "LCDPort" "LVDS0"
EndSection

Section "Screen"
    Identifier "Screen0"
    Device     "Card0"
    DefaultDepth 24
    SubSection "Display"
        Modes      "1280x800"
        Depth     24
    EndSubSection
EndSection
```

---

### Post by lord_wenk on 2010-09-21
thanks for making hope for VIA Chrome9 IGP users...

but i have been trying to use your xorg.conf for my VN896 Display.
But it is not working. Cannot enter the gui mode, and ubuntu system tells me to use failsafe which mean unload the invalid driver.

So i uninstalled it.

May be you can help me how to configure xorg.conf for my VN896 ??
The laptop screen is 1440 x 900 px

Thank you.

---

