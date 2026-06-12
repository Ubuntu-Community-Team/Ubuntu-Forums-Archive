---
title: "No sound on my DVI-HDMI connected TV- Nvidia 9500"
date: 2009-08-19
forum: General Help
---

### Post by rcpinchey on 2009-08-19
Right, the problem here is that the EDID supplied by my HD TV tells the Nvidia drivers that it's connected over HDMI and would very much like to be sent some audio data. The Nvidia driver, as you would expect, then tries to send said audio data- however, as the HDMI cable is connected to the DVI socket on the card via a converter, it doesn't manage it. The TV is hence being told it's receiving audio, but isn't, so happily ignores the audio it's ACTUALLY being sent via the attached phono cable.

I've fixed this problem already under Vista, where it was relatively easy. Under Ubuntu, however, not so much.

I've tried a custom EDID with the specific data stripped, as suggested here:
[http://ubuntuforums.org/showthread.php?t=951107](http://ubuntuforums.org/showthread.php?t=951107)

The same suggestion is given here, along with a summary of the problem:
[http://www.mythtv.org/wiki/Configuring_Analog_Sound_DVI_to_HDMI](http://www.mythtv.org/wiki/Configuring_Analog_Sound_DVI_to_HDMI)

No luck when I tried it- I got the display working, but not the sound.


Now, I've tried generating my own modeline and instructing the xserver to ignore the EDID entirely, resulting in the xorg.conf below:

```

Section "ServerLayout"
    Identifier     "Default Layout"
    Screen      0  "Screen0" 1360 0
    Screen      1  "Screen1" LeftOf "Screen0"
    InputDevice    "Keyboard0" "CoreKeyboard"
    InputDevice    "Mouse0" "CorePointer"
EndSection

Section "Module"
    Load           "glx"
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
    ModelName      "Samsung SyncMaster"
    HorizSync       30.0 - 81.0
    VertRefresh     56.0 - 60.0
EndSection

Section "Monitor"
    Identifier     "Monitor1"
    VendorName     "Unknown"
    ModelName      "SONY TV"
    Modeline       "1360x768_60.00"  84.72  1360 1424 1568 1776  768 769 772 795  -HSync +Vsync
    HorizSync       14.0 - 68.0
    VertRefresh     48.0 - 62.0
EndSection

Section "Device"
    Identifier     "Configured Video Device"
    Driver         "nvidia"
    Option         "NoLogo" "True"
EndSection

Section "Device"
    Identifier     "Device0"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "GeForce 9500 GT"
    BusID          "PCI:3:0:0"
    Screen          0
EndSection

Section "Device"
    Identifier     "Device1"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "GeForce 9500 GT"
    BusID          "PCI:3:0:0"
    Screen          1
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
    Option         "TwinViewXineramaInfoOrder" "CRT-1"
    Option         "metamodes" "CRT: nvidia-auto-select +0+0"
    SubSection     "Display"
        Depth       24
    EndSubSection
EndSection

Section "Screen"
    Identifier     "Screen1"
    Device         "Device1"
    Monitor        "Monitor1"
    DefaultDepth    24
    Option         "UseEDID" "False"
    Option         "ExactModeTimingsDVI" "True"
    Option         "TwinView" "0"
    Option         "metamodes" "DFP: nvidia-auto-select +0+0"
    SubSection     "Display"
        Depth       24
    EndSubSection
EndSection

```That doesn't work either. The picture's the right size and shape and the TV isn't on fire, but there's still no damn sound.

This is driving me nuts, and it's only the last grain of hope that maybe someone on these forums will be able to help that's stopping me snapping the Ubuntu CD in two pieces and going back to the friendly arms of Microsoft permanently.

Does anyone know what's wrong with my xorg.conf? Does anyone have any suggestions of how to proceed from here?

---

### Post by rcpinchey on 2009-08-20
Oops, I probably should have mentioned, this is Jaunty Jackalope. Of course, this means ctrl-alt-backspace doesn't work, so I'm restarting my entire machine every time I tweak the config file- which is not doing wonders for my mood now I'm about 100 iterations in.  :-(

---

### Post by rcpinchey on 2009-08-20
Do I take it from the deafening silence that no-one else has any idea what is wrong or what to do next?

I honestly thought that the thought of a frustrated man giving up on Ubuntu and returning to the easier-to-use Vista would spur at least ONE forum user into attempting to help, but it looks like I was overly optimistic.

I can't think of anything else to try, and can't find any further suggestions online, so unless someone decides to throw me a lifeline I'm officially giving up.

---

### Post by x C0MMAND0 x on 2009-08-20
[http://www.ubuntugeek.com/howto-enable-ctrl-alt-backspace-in-ubuntu-jaunty.html](http://www.ubuntugeek.com/howto-enable-ctrl-alt-backspace-in-ubuntu-jaunty.html)

^^^
Enable ctrl-alt-backspace

---

### Post by rcpinchey on 2009-08-20
Ah, thanks! That'll make the process of trying out any further workarounds MUCH less painful! All I need now are any further workarounds...    :-S

---

