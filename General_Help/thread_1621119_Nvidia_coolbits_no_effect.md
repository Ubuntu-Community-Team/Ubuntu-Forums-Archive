---
title: "Nvidia coolbits no effect"
date: 2010-11-13
forum: General Help
---

### Post by reffu on 2010-11-13
I think this is a problem related to Maverick (or the latest Nvidia drivers which are installed in maverick). I enabled coolbits in my xorg.conf and the clock frequencies are available in nvidia-settings. However, whenever I attempt to change anything the slider will move but when I click apply it will revert back to its default value. I have a geforce GT 220 and overclocking worked fine in 10.04. Any help would be greatly appreciated.

```
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
    VendorName     "Acer"
    ModelName      "Acer AL2216W"
    HorizSync       31.0 - 84.0
    VertRefresh     56.0 - 77.0
    Option         "DPMS"
EndSection

Section "Device"
    Identifier     "Device0"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "GeForce GT 220"
    Option "Coolbits" "1"
EndSection

Section "Screen"

# Removed Option "metamodes" "DFP: nvidia-auto-select +0+0, CRT: nvidia-auto-select +1680+0"
# Removed Option "TwinView" "1"
# Removed Option "metamodes" "CRT: nvidia-auto-select +1680+0, DFP: nvidia-auto-select +0+0"
    Identifier     "Screen0"
    Device         "Device0"
    Monitor        "Monitor0"
    DefaultDepth    24
    Option         "TwinView" "0"
    Option         "TwinViewXineramaInfoOrder" "DFP-0"
    Option         "metamodes" "DFP: nvidia-auto-select +0+0"
    SubSection     "Display"
        Depth       24
    EndSubSection
EndSection

```

---

### Post by Kenzy88 on 2010-11-27
I have the same problem. Reported the bug here:
[https://bugs.launchpad.net/ubuntu/+source/nvidia-settings/+bug/682143](https://bugs.launchpad.net/ubuntu/+source/nvidia-settings/+bug/682143)

---

### Post by rico9999 on 2010-11-27
I know this is a Ubuntu forum, but I'm seeing an identical issue in Fedora 14 with NVIDIA-Linux-x86-260.19.21 and integrated MCP79 (Geforce 9300).

---

### Post by iNsOmNiOuS on 2010-11-27
I also have the same problem also with a GeForce 9300

Would love to find a solution to this

---

### Post by rico9999 on 2010-11-27
Same issue with NVIDIA-Linux-x86-256.53 on FC14.

I tried going back to NVIDIA-Linux-x86-195.36.15 but the old driver wouldn't load.

---

### Post by steve29 on 2010-11-29
> **iNsOmNiOuS said:**
> I also have the same problem also with a GeForce 9300 Would love to find a solution to this

Same issue with Ubuntu 10.10 / Nvidia drivers 260.19.21 
and a 6600GT/128Mo DDR3 AGP card .
Coolbit seems ineffective .
The "apply" result even sometimes in
ramdon speed for gpu/memory ! 
But mainly the settting are definitely not effective. 
( i was looking for a Underclock in 3D mode due to ramdon
crash in FPS game like ET, UrbanAssault, Nexus ...but had least
no problem in 2D mode ).

---

### Post by steve29 on 2010-12-03
> **steve29 said:**
> Same issue with Ubuntu 10.10 / Nvidia drivers 260.19.21 
and a 6600GT/128Mo DDR3 AGP card .
Coolbit seems ineffective .
The "apply" result even sometimes in
ramdon speed for gpu/memory ! 
But mainly the settting are definitely not effective. 
( i was looking for a Underclock in 3D mode due to ramdon
crash in FPS game like ET, UrbanAssault, Nexus ...but had least
no problem in 2D mode ).

yesterday the system updated for the xorg/nvidia server 260.19.26 and it seems the issue has been solved .It works, now the only limitation i've still got it's the DDR Memory speed in between 2D & 3D application
It is linked ( sorry for my poor english ) i mean by that : i cannot configure a different clock for 3D & 2D .

In revenge the GPU clock can be different ( thank god !:^)
It has solved my problem of system crash when playing 3D FPS
games (lite ET:wolfenstein, Nexus...) only by decreasing the speed of my DDR3 from 900Mhz to 800Mhz ( Nvidia 6600GT ).
Hope it Helps !

---

### Post by steve29 on 2011-05-13
Hi All
To the request of UK-fatality (sorry for the delay , got to end my thesis first !) here's the solution to make nvidia coolbit setting persistant ! it's easy ( i'm not a Linux Guru!) and it works ! Have Fun & Hope it Helps !
Antonio 
PS : Of course for reals newbies , don't forgot to add the : option  "coolbits" "1" 
 in the device section of xorg.conf ..!!
---------------------------

Nice one. Can you post this to the thread so others can use this feature.

Cheers

Quote:
Originally Posted by steve29
Quote:
Originally Posted by fatality_uk
Hi Steve,

Sorry haven't managed to find a solution yet. I just have to enable when I play games.

Cheers
George
Well ...good news ! i did it !
i just wrote a txt file call Nvidia-clock-setting.txt , save it in my home directory 
what inside ? :

nvidia-settings -a GPUOverclockingState=1 
-a GPU2DClockFreqs=200,400 
-a GPU3DClockFreqs=400,400

That's all ( my nvidia 7900gt is 470GPU 685RAM clock by default ) 
Then open "system" "pref" "startup program" and add a line launching the file at each boot ! it works ! 
Hope it helps !

---

### Post by spinifex on 2011-06-27
I'm looking at enabling coolbits in my xorg.conf too. 

After googling I have come across several variations of coolbits [here]("http://ncatarino.net/archives/573") and [here]("http://us.download.nvidia.com/XFree86/Linux-x86/195.36.24/README/xconfigoptions.html"); namely,
[B]
option "coolbits" "[COLOR="Red"][SIZE="4"]1[/SIZE][/COLOR]" or option "coolbits" "[COLOR="#ff0000"][SIZE="4"]4[/SIZE][/COLOR]"  or  option "coolbits" "[COLOR="#ff0000"][SIZE="4"]5[/SIZE][/COLOR]"[/B]

I'm just wondering which version or setting I would use in Fedora 15?  Does the same apply to Ubuntu?  

What is the difference between the various numbers specified in **option "coolbits" "[COLOR="Red"][B][SIZE="4"]*[/SIZE]**[/COLOR]"[/B]

Which should I use?  And, is anyone else even aware of this?

---

