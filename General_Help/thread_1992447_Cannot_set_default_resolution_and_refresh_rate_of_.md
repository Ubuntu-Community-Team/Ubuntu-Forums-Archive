---
title: "Cannot set default resolution and refresh rate of my screen again."
date: 2012-05-31
forum: General Help
---

### Post by Jot-z on 2012-05-31
More than year ago I tried to use Ubuntu but I had to give up due to issue with setting resolution and refresh rate. I described problem, looked for solution and then asked here on the forum for help and came back to Windows as nobody was able to solve the problem.

You can find my old thread about the issue here [http://ubuntuforums.org/showthread.php?t=1744267](http://ubuntuforums.org/showthread.php?t=1744267).

Now, after more than a year I have installed Ubuntu and I can't set default resolution and refresh rate of my screen again (I still have the same hardware - GeForce 430 GT, Acer AL1916). I'm really amazed that such a important issue like this haven't been fixed for a year or more.

I have tried to do same things I did last time when I tried to fix the issue. Except that I have done following:[INDENT]cvt 1280 1024 75
# 1280x1024 74.90 Hz (CVT 1.31M4) hsync: 80.30 kHz; pclk: 138.75 MHz
Modeline "1280x1024_75.00"  138.75  1280 1368 1504 1728  1024 1027 1034 1072 -hsync +vsync

xrandr
xrandr: Failed to get size of gamma for output default
Screen 0: minimum 320 x 240, current 1024 x 768, maximum 1024 x 768
default connected 1024x768+0+0 0mm x 0mm
   1024x768       50.0* 
   800x600        51.0     52.0     53.0  
   680x384        54.0     55.0  
   640x480        56.0  
   512x384        57.0  
   400x300        58.0  
   320x240        59.0 

xrandr --newmode "1280x1024_75.00"  138.75  1280 1368 1504 1728  1024 1027 1034 1072 -hsync +vsync
xrandr: Failed to get size of gamma for output default

xrandr --addmode default 1280x1024_75.00
xrandr: Failed to get size of gamma for output default

xrandr --output default --mode 1280x1024_75.00
xrandr: Failed to get size of gamma for output default
xrandr: screen cannot be larger than 1024x768 (desired size 1280x1024)

jot@Desktop-AMD:~$ sudo dpkg-reconfigure xserver-xorg

jot@Desktop-AMD:~$ xrandr --output default --mode 1280x1024_75.00
xrandr: Failed to get size of gamma for output default
xrandr: Configure crtc 0 failed
[/INDENT]I'm asking for help again but I'll be surprised if someone is able to help me with solving that problem here. I'll probably have to get used to this crappy resolution as coming back to Windows is out of question.

Are there any places except this forum and Ubuntu IRC where I may report the issue to developers and ask for sufficient help?

---

### Post by irv on 2012-05-31
Are you trying or have you loaded any proprietary drivers for this hardware? And if you have, have you tried your display without loading them? I don't know anything about your display card but I thought I would just throw this out here. Maybe someone else has the same hardware or close to it that might be able to help.

---

### Post by Jot-z on 2012-05-31
> **irv said:**
> Are you trying or have you loaded any proprietary drivers for this hardware? And if you have, have you tried your display without loading them? I don't know anything about your display card but I thought I would just throw this out here. Maybe someone else has the same hardware or close to it that might be able to help.

I'm using proprietary drivers at the moment. I have experienced the same issue without them and on live CD. IMO there's something wrong with screen recognition and it limits maximal resolution to 1024x768. Now my screen is called 'Laptop' in display setting. It was called 'CRT-0' when I tried Ubuntu year ago.

---

### Post by irv on 2012-05-31
I'm not sure what this will tell you but I ran across this.
Dynamically testing different resolutions
[https://wiki.ubuntu.com/X/Config/Resolution#Dynamically_testing_different_resolutions]("https://wiki.ubuntu.com/X/Config/Resolution#Dynamically_testing_different_resolutions")
Here is another place to look.
[https://help.ubuntu.com/community/BinaryDriverHowto]("https://help.ubuntu.com/community/BinaryDriverHowto")

---

### Post by CatKiller on 2012-06-01
> **Jot-z said:**
> I'm really amazed that such a important issue like this haven't been fixed for a year or more.

I don't see why; you're still using the same broken monitor.

You were on the right track before, but goodness knows where you got those numbers from. The appropriate values for that monitor, according to the specs, are

```
    HorizSync       30-82
    VertRefresh     56-76
```Also, 50Hz wasn't hurting your eyes both because it wasn't running at 50Hz and because refresh rate is meaningless for an LCD.

---

### Post by Jot-z on 2012-06-01
> **irv said:**
> I'm not sure what this will tell you but I ran across this.
Dynamically testing different resolutions
[https://wiki.ubuntu.com/X/Config/Resolution#Dynamically_testing_different_resolutions](https://wiki.ubuntu.com/X/Config/Resolution#Dynamically_testing_different_resolutions)
Here is another place to look.
[https://help.ubuntu.com/community/BinaryDriverHowto](https://help.ubuntu.com/community/BinaryDriverHowto)

I'm afraid that I don't understand how it would help to solve the problem. I have already tried using xrandr commands to set resolution and it failed. I use NVIDIA drivers (I have written about it in my previous posts).

> **CatKiller said:**
> I don't see why; you're still using the same broken monitor.

You were on the right track before, but goodness knows where you got  those numbers from. The appropriate values for that monitor, according  to the specs, are

```
    HorizSync       30-82
    VertRefresh     56-76
```Also, 50Hz wasn't hurting your eyes both  because it wasn't running at 50Hz and because refresh rate is  meaningless for an LCD.

Could you explain how my monitor is broken? It's properly detected on Windows and I can set its default resolution and 75Hz refresh rate on Windows. If the issue is really caused by monitor, I'll send it to service centre or try to buy new one. A few years ago when I tried older Ubuntu versions I could also set default resolution of my monitor.

If you found mistake in xrandr commands which I typed, could you correct me or explain me what I need to do, please? I don't understand what I have done wrong.

---

### Post by CatKiller on 2012-06-01
> **Jot-z said:**
> 
Could you explain how my monitor is broken? 

Even though the mechanism to correctly identify your monitor and advertise its capabilities has been in existence for nearly 20 years, your monitor doesn't have it, relying instead on a Windows "driver" that's simply a text file containing the information that should have been transmitted through EDID. Broken.

---

### Post by Jot-z on 2012-06-01
> **CatKiller said:**
> Even though the mechanism to correctly identify your monitor and advertise its capabilities has been in existence for nearly 20 years, your monitor doesn't have it, relying instead on a Windows "driver" that's simply a text file containing the information that should have been transmitted through EDID. Broken.

Are there any workarounds to allow Linux to identify the monitor properly?

---

### Post by CatKiller on 2012-06-01
> **Jot-z said:**
> Are there any workarounds to allow Linux to identify the monitor properly?

Yes. You can either tell X the correct refresh rates by modifying xorg.conf, which is what you were doing before albeit with the wrong values, or you can create a new mode for XRandR with timing information. I can probably help a bit with the first option (which is slightly less flexible) or someone else can probably help with the second option that I am less familiar with.

---

### Post by Jot-z on 2012-06-01
> **CatKiller said:**
> Yes. You can either tell X the correct refresh rates by modifying xorg.conf, which is what you were doing before albeit with the wrong values, or you can create a new mode for XRandR with timing information. I can probably help a bit with the first option (which is slightly less flexible) or someone else can probably help with the second option that I am less familiar with.

It would be great if you helped me.

That's my xorg.conf:[INDENT]# nvidia-settings: X configuration file generated by nvidia-settings
# nvidia-settings:  version 295.33  (buildd@allspice)  Fri Mar 30 13:37:33 UTC 2012

Section "ServerLayout"
    Identifier     "Layout0"
    Screen      0  "Screen0" 0 0
    InputDevice    "Keyboard0" "CoreKeyboard"
    InputDevice    "Mouse0" "CorePointer"
    Option         "Xinerama" "0"
EndSection

Section "Files"
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

Section "InputDevice"
    # generated from default
    Identifier     "Keyboard0"
    Driver         "kbd"
EndSection

Section "Monitor"
    # HorizSync source: builtin, VertRefresh source: builtin
    Identifier     "Monitor0"
    VendorName     "Unknown"
    ModelName      "CRT-1"
    HorizSync       28.0 - 55.0
    VertRefresh     43.0 - 72.0
    Option         "DPMS"
EndSection

Section "Device"
    Identifier     "Device0"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "GeForce GT 430"
EndSection

Section "Screen"
    Identifier     "Screen0"
    Device         "Device0"
    Monitor        "Monitor0"
    DefaultDepth    24
    Option         "TwinView" "0"
    Option         "TwinViewXineramaInfoOrder" "CRT-1"
    Option         "metamodes" "nvidia-auto-select +0+0"
    SubSection     "Display"
        Depth       24
    EndSubSection
EndSection

[/INDENT]What do I need to change or insert?

---

### Post by LinGNUbie on 2012-06-01
I am not familiar with your monitor, however I have had many problems with using the Nvidia settings along with xrandr to set resolutions. I have often found it easier to create a proper xorg.conf to configure my display.

Using the information you have provided and the Modeline generator at [www.arachnoid.com/modelines/index.html]("www.arachnoid.com/modelines/index.html"), I came up with the following xorg.conf. Bear in mind, I will not be responsible for any adverse effects that may occur, so use at your own risk.

First backup your current config, then replace xorg.conf with the following;

```

# EXPERIMENTAL xorg.conf

Section "ServerLayout"
Identifier "Layout0"
Screen 0 "Screen0" 0 0
InputDevice "Keyboard0" "CoreKeyboard"
InputDevice "Mouse0" "CorePointer"
Option "Xinerama" "0"
EndSection

Section "Files"
EndSection

Section "InputDevice"
# generated from default
Identifier "Mouse0"
Driver "mouse"
Option "Protocol" "auto"
Option "Device" "/dev/psaux"
Option "Emulate3Buttons" "no"
Option "ZAxisMapping" "4 5"
EndSection

Section "InputDevice"
# generated from default
Identifier "Keyboard0"
Driver "kbd"
EndSection

Section "Monitor"
Identifier "Monitor0"
VendorName "Acer"
ModelName "AL1916W"
HorizSync	30.0 - 82.0
VertRefresh	56.0 - 76.0
Option "DPMS"
Modeline "640x480_60.00" 23.86 640 656 720 800 480 481 484 497 -HSync +Vsync
Modeline "800x600_60.00" 38.22 800 832 912 1024 600 601 604 622 -HSync +Vsync
Modeline "1024x768_60.00" 64.11 1024 1080 1184 1344 768 769 772 795 -HSync +Vsync
Modeline "1024x768_75.00" 81.80 1024 1080 1192 1360 768 769 772 802 -HSync +Vsync
Modeline "1152x768_60.00" 71.74 1152 1208 1328 1504 768 769 772 795 -HSync +Vsync
Modeline "1152x768_75.00" 92.39 1152 1224 1344 1536 768 769 772 802 -HSync +Vsync
Modeline "1360x768_60.00" 84.72 1360 1424 1568 1776 768 769 772 795 -HSync +Vsync
Modeline "1360x768_75.00" 108.75 1360 1440 1584 1808 768 769 772 802 -HSync +Vsync
Modeline "1280x1024_60.00" 108.88 1280 1360 1496 1712 1024 1025 1028 1060 -HSync +Vsync
Modeline "1280x1024_75.00" 138.54 1280 1368 1504 1728 1024 1025 1028 1069 -HSync +Vsync
Modeline "1280x1024_80.00" 149.57 1280 1376 1512 1744 1024 1025 1028 1072 -HSync +Vsync
Modeline "1440x900_60.00" 106.47 1440 1520 1672 1904 900 901 904 932 -HSync +Vsync
Modeline "1440x900_75.00" 136.49 1440 1536 1688 1936 900 901 904 940 -HSync +Vsync
EndSection

Section "Device"
Identifier "Device0"
Driver "nvidia"
VendorName "NVIDIA Corporation"
BoardName "GeForce GT 430"
EndSection

Section "Screen"
Identifier "Screen0"
Device "Device0"
Monitor "Monitor0"
DefaultDepth 24
Option "TwinView" "0"
SubSection "Display"
Depth 24
Modes	"1440x900@75"	"1440x900@60"	"1280x1024@80"	"1280x1024@75"	"1280x1024@60"	"1360x768@75"	"1360x768@60"	"1152x768@75"	"1152x768@60"	"1024x768@75"	"1024x768@60"	"800x600@60"	"640x480@60"
EndSubSection
EndSection

```

Reboot, and use the standard monitor control panel via desktop to try and set resolution from there.

---

### Post by Jot-z on 2012-06-01
Thank you all for successful help and explaining the issue. 

I have succeed to set default resolution of my screen using the xorg.conf file posted above :D

---

### Post by LinGNUbie on 2012-06-01
No problem, we're all here to help each other out! Remember to mark the thread as solved using the thread tools.

---

