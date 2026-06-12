---
title: "Ubuntu 10.04 x64 / Nvidia Quadro NVS / Dell E6500 /"
date: 2010-05-21
forum: General Help
---

### Post by swappa on 2010-05-21
I am posting this to hear if there are others with display issues on Dell E6500 laptop with the Nvidia Quadro NVS 160 driver. This problem is starting to annoy me a great deal, but I am uncertain how I should move forward. In short;

I have Ubuntu 10.04 x64 installed on my Dell E6500 laptop. When using only the laptop, everything works great. The second I plug it into the docking station (the laptop lid closed) and want to use my two external monitors (Dell 2001FP) I'm in trouble. I cant see anything and what I get is a 'DVI: Cannot Display this Mode' on the primary monitor - If i try a regular VGA cable I get nothing but a black screen. 

I have played around with the Nvidia config but it cant find my monitors and therefore I cant do much. I am aware of the various "hack the xorg.conf" options, but I before I do that I wanted to see if others had experienced the same thing. I had hoped that we were pasted the hack stage and that primary functions such as display would work by now.

---

### Post by weijiajun on 2010-06-01
I have the same laptop and have the same issue you were talking about.  I only use one monitor with my dock but still.  I found that it would recognize the external monitor on the dock by default until I install the nvidia drivers.  Once that happened nothing showed up.  

For me the way I fixed this was to play with the metamodes in the xorg.conf (I know you don't want to hack but it works.)  Basically I setup the external monitor as the default to use if available and that the default metamode has the internal (laptop screen) turned off.  Then I setup 3 key commands which when executed will run xrandr -s MODE to switch between laptop only monitor, dual mode and finally external only.  I know it seems more like a hack then anything but I have really enjoyed it and it has worked out really well.  

I can paste my metamodes if you want to see them, just let me know.

---

### Post by swappa on 2010-06-02
> **weijiajun said:**
> I have the same laptop and have the same issue you were talking about.  I only use one monitor with my dock but still.  I found that it would recognize the external monitor on the dock by default until I install the nvidia drivers.  Once that happened nothing showed up.  

For me the way I fixed this was to play with the metamodes in the xorg.conf (I know you don't want to hack but it works.)  Basically I setup the external monitor as the default to use if available and that the default metamode has the internal (laptop screen) turned off.  Then I setup 3 key commands which when executed will run xrandr -s MODE to switch between laptop only monitor, dual mode and finally external only.  I know it seems more like a hack then anything but I have really enjoyed it and it has worked out really well.  

I can paste my metamodes if you want to see them, just let me know.

Thanks for your reply. I dont mind hacking it as a last resort. Please post your metamodes :-) 

Again, thank you.

---

### Post by ibates on 2010-06-02
This reply probably won't do a lot by way of helping you, but it might just shine a little more light on the nature of the beast.

I do not have the system you mention, but for years I have been haunted by a randomly hanging desktop (an ASUS by the way).  I have nearly thrown it out the window on many an occasion, but for one reason or another, stuck with it.

Recently I decided that, in order to rid my system of the "bug" that was undoubtedly there, I would do a clean re-install right from scratch.  Ubuntu 10.04 LTS came along just at the right time and that is the one I installed from scratch.

So far so good.  Everything worked a treat - until I installed the NVidia drivers.  Within minutes, I had that damned "hang" again.  It is not actually a hang, but a loss of control of the mouse, keyboard and monitor.  Sometimes the system seems to continue on  (the clock runs), but sometimes the whole shebang closes down.

So without further ado (no other software had been added to the clean install at that point), I smartly removed the NVidia drivers.  There has been no further trouble.

For what it is worth, perhaps NVidia drivers and Ubuntu are simply not compatible bedfellows.

---

### Post by swappa on 2010-06-02
> **ibates said:**
> This reply probably won't do a lot by way of helping you, but it might just shine a little more light on the nature of the beast.

I do not have the system you mention, but for years I have been haunted by a randomly hanging desktop (an ASUS by the way).  I have nearly thrown it out the window on many an occasion, but for one reason or another, stuck with it.

Recently I decided that, in order to rid my system of the "bug" that was undoubtedly there, I would do a clean re-install right from scratch.  Ubuntu 10.04 LTS came along just at the right time and that is the one I installed from scratch.

So far so good.  Everything worked a treat - until I installed the NVidia drivers.  Within minutes, I had that damned "hang" again.  It is not actually a hang, but a loss of control of the mouse, keyboard and monitor.  Sometimes the system seems to continue on  (the clock runs), but sometimes the whole shebang closes down.

So without further ado (no other software had been added to the clean install at that point), I smartly removed the NVidia drivers.  There has been no further trouble.

For what it is worth, perhaps NVidia drivers and Ubuntu are simply not compatible bedfellows.

Yeah, thinking you're right. I do have a lot of smaller annoyances that can be blamed on the graphics driver. However, I feel the performance (when everything is working) is better with the proprietary driver. On my home computer I am running a single 22 inch screen setup with a GTS 8800 card (still Nvidia drivers) and it is blazingly fast with no issues what so ever. The problems I am describing are all happening on my laptop.

---

### Post by Espenfe on 2010-06-02
I got the same problem on a E6400 with the same gfx card. If you could post your metamode hacks it would be great!

---

### Post by Espenfe on 2010-06-11
Still having problems with configuring this the rigth way. I have been able to make two metamodes that uses either the laptop display or one of my two external monitors. 

I also have been sucessfull in using the xrandr -s command to change between the displays.

Looking at /var/log/Xorg.0.conf show why it fails though:

```
(WW) Jun 11 16:13:51 NVIDIA(0): There are only 2 heads available, trimming display device list
(WW) Jun 11 16:13:51 NVIDIA(0):     from "DFP-0, DFP-1, DFP-2" to "DFP-0, DFP-1".
(II) Jun 11 16:13:52 NVIDIA(0): Assigned Display Devices: DFP-0, DFP-1
(WW) Jun 11 16:13:52 NVIDIA(0): Invalid display device in Mode Description
(WW) Jun 11 16:13:52 NVIDIA(0):     "DFP-2:1920x1200+0+0"
(WW) Jun 11 16:13:52 NVIDIA(0): Not using mode description "DFP-2:1920x1200+0+0"; unable to
(WW) Jun 11 16:13:52 NVIDIA(0):     map to display device
(WW) Jun 11 16:13:52 NVIDIA(0): Invalid display device in Mode Description "DFP-2:NULL"
(WW) Jun 11 16:13:52 NVIDIA(0): Not using mode description "DFP-2:NULL";
```




My xorg.conf looks like this:

```
# nvidia-settings: X configuration file generated by nvidia-settings
# nvidia-settings:  version 1.0  (buildd@yellow)  Fri Apr  9 11:51:21 UTC 2010


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

    # HorizSync source: edid, VertRefresh source: edid
    Identifier     "Monitor0"
    VendorName     "Unknown"
    ModelName      "LPL"
    HorizSync       30.0 - 75.0
    VertRefresh     40.0 - 60.0
    Option         "DPMS"
EndSection

Section "Device"
    Identifier     "Device0"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "Quadro NVS 160M"
EndSection

Section "Screen"

    Identifier     "Screen0"
    Device         "Device0"
    Monitor        "Monitor0"
    DefaultDepth    24
    Option         "TwinView" "1"
    Option         "TwinViewXineramaInfoOrder" "DFP-2"
    Option         "metamodes" "DFP-0: NULL, DFP-1: 1920x1200 +1920+0, DFP-2: 1920x1200 +0+0; DFP-0: 1440x900 +0+0, DFP-1: NULL, DFP-2: NULL"
    SubSection     "Display"
        Depth       24
    EndSubSection
EndSection

```

Can someone point me in the rigth direction? ;-)

---

### Post by swappa on 2010-06-15
> **Espenfe said:**
> Still having problems with configuring this the rigth way. I have been able to make two metamodes that uses either the laptop display or one of my two external monitors. 

I also have been sucessfull in using the xrandr -s command to change between the displays.

Looking at /var/log/Xorg.0.conf show why it fails though:

```
(WW) Jun 11 16:13:51 NVIDIA(0): There are only 2 heads available, trimming display device list
(WW) Jun 11 16:13:51 NVIDIA(0):     from "DFP-0, DFP-1, DFP-2" to "DFP-0, DFP-1".
(II) Jun 11 16:13:52 NVIDIA(0): Assigned Display Devices: DFP-0, DFP-1
(WW) Jun 11 16:13:52 NVIDIA(0): Invalid display device in Mode Description
(WW) Jun 11 16:13:52 NVIDIA(0):     "DFP-2:1920x1200+0+0"
(WW) Jun 11 16:13:52 NVIDIA(0): Not using mode description "DFP-2:1920x1200+0+0"; unable to
(WW) Jun 11 16:13:52 NVIDIA(0):     map to display device
(WW) Jun 11 16:13:52 NVIDIA(0): Invalid display device in Mode Description "DFP-2:NULL"
(WW) Jun 11 16:13:52 NVIDIA(0): Not using mode description "DFP-2:NULL";
```




My xorg.conf looks like this:

```
# nvidia-settings: X configuration file generated by nvidia-settings
# nvidia-settings:  version 1.0  (buildd@yellow)  Fri Apr  9 11:51:21 UTC 2010


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

    # HorizSync source: edid, VertRefresh source: edid
    Identifier     "Monitor0"
    VendorName     "Unknown"
    ModelName      "LPL"
    HorizSync       30.0 - 75.0
    VertRefresh     40.0 - 60.0
    Option         "DPMS"
EndSection

Section "Device"
    Identifier     "Device0"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "Quadro NVS 160M"
EndSection

Section "Screen"

    Identifier     "Screen0"
    Device         "Device0"
    Monitor        "Monitor0"
    DefaultDepth    24
    Option         "TwinView" "1"
    Option         "TwinViewXineramaInfoOrder" "DFP-2"
    Option         "metamodes" "DFP-0: NULL, DFP-1: 1920x1200 +1920+0, DFP-2: 1920x1200 +0+0; DFP-0: 1440x900 +0+0, DFP-1: NULL, DFP-2: NULL"
    SubSection     "Display"
        Depth       24
    EndSubSection
EndSection

```

Can someone point me in the rigth direction? ;-)

Thanks. I am closer, but still dont see a fat Cuban sigar :-) 
Will play around with some more. Thanks.

---

### Post by Schuby007 on 2010-10-31
> **weijiajun said:**
> I have the same laptop and have the same issue you were talking about.  I only use one monitor with my dock but still.  I found that it would recognize the external monitor on the dock by default until I install the nvidia drivers.  Once that happened nothing showed up.  

For me the way I fixed this was to play with the metamodes in the xorg.conf (I know you don't want to hack but it works.)  Basically I setup the external monitor as the default to use if available and that the default metamode has the internal (laptop screen) turned off.  Then I setup 3 key commands which when executed will run xrandr -s MODE to switch between laptop only monitor, dual mode and finally external only.  I know it seems more like a hack then anything but I have really enjoyed it and it has worked out really well.  

I can paste my metamodes if you want to see them, just let me know.

Hi,

I'm new to Linux. I got tired of Windows and installed Ubuntu 10.04 64-bit on my Alienware m15x laptop. The laptop has an Nvidia GeForce 8800M GTX gpu; I'm using NVIDIA Driver Version: 195.36.24 (recommended by "Hardware Drivers").

At home I connect my laptop to my external monitor via HDMI and use the external by itself. In order to get the external display working I had to enter Nvidia settings and enable the external display and then disable the laptop display and restart. I then had to edit gnome power settings to set lid-close action to "Do Nothing" because when I went to close my laptop display, it would blank my external monitor as well. This is fine for when I'm working at home, although I've noticed that the screensaver won't work on the external unless the laptop display is up. I have no idea why?

The problem is when I have to change locations... I have to enter nvidia-settings, enable the laptop display, disable the external display and restart. It's a royal pain in the ***...

I was hoping you might be able to help me setup something that automates with metamodes....

My /etc/X11/xorg.conf file:
```

# nvidia-settings: X configuration file generated by nvidia-settings
# nvidia-settings:  version 1.0  (buildd@yellow)  Fri Apr  9 11:51:21 UTC 2010


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

    # HorizSync source: edid, VertRefresh source: edid
    Identifier     "Monitor0"
    VendorName     "Unknown"
    ModelName      "Dell Alienware2210"
    HorizSync       30.0 - 83.0
    VertRefresh     56.0 - 76.0
    Option         "DPMS"
EndSection

Section "Monitor"

    # HorizSync source: edid, VertRefresh source: edid
    Identifier     "Monitor1"
    VendorName     "Unknown"
    ModelName      "Dell Alienware2210"
    HorizSync       30.0 - 83.0
    VertRefresh     56.0 - 76.0
    Option         "DPMS"
EndSection

Section "Device"
    Identifier     "Device0"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "GeForce 8800M GTX"
    Option "RegistryDwords" "PowerMizerEnable=0×1; PerfLevelSrc=0×3322; PowerMizerDefaultAC=0×1" 
EndSection

Section "Device"
    Identifier     "Device1"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "GeForce 8800M GTX"
    BusID          "PCI:1:0:0"
    Screen          1
EndSection

Section "Screen"

# Removed Option "metamodes" "DFP-0: nvidia-auto-select +0+0"
    Identifier     "Screen0"
    Device         "Device0"
    Monitor        "Monitor0"
    DefaultDepth    24
    Option         "TwinView" "0"
    Option         "metamodes" "DFP-1: nvidia-auto-select +0+0"
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
    Option         "metamodes" "DFP-1: nvidia-auto-select +0+0"
    SubSection     "Display"
        Depth       24
    EndSubSection
EndSection

```

The only part of the xorg.conf file that I edited was I added   "Option "RegistryDwords" "PowerMizerEnable=0×1; PerfLevelSrc=0×3322; PowerMizerDefaultAC=0×1"" under "Section "Device"" for "Device 0". This line disables the Nvidia gpu throttling when on ac power and enables it on battery.

I have looked around at a lot of forums and problems like this and I can't find any solutions that translate. Any help would be greatly appreciated.

Thankyou

---

### Post by swappa on 2010-11-01
I was able to fix my problem following this guide - [http://www.blog.arun-prabha.com/2009/10/21/dual-monitor-in-ubuntu-linux/](http://www.blog.arun-prabha.com/2009/10/21/dual-monitor-in-ubuntu-linux/)  - fixed my dual monitor setup too. 

Unbelievable that things like this still doesn't work out of the box yet ...

---

### Post by Schuby007 on 2010-11-01
Another problem...

When at home using my external display only, the screen saver doesn't work. It's weird, cause the screen goes dark after 5 minutes (which is what I set in screen saver settings) and it asks for password when I shake the mouse (which is what I want) but I don't get the actual screen saver.

As well, I have gnome-power-management set to put display to sleep after 30 minutes. This doesn't work with my external.

NOTE: I found that if I have my laptop screen up (not closed), the screen saver will work on the external. Haven't tested yet whether having the laptop lid open will allow the external to go to sleep after 30 mins.

It seems to me that the gnome-screensaver and power management are getting confused between my internal and external monitors. Perhaps it could be because display settings are handled by nvidia-settings?? If thats the case then I consider it bad practise for Ubuntu to include the proprietary nvidia drivers without proper support.

I'd be very interested in knowing if anyone else is having this problem. And would be thrilled if anyone had any solutions.

Thankyou.

---

