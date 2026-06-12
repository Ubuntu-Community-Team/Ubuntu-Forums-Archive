---
title: "Switch between single/dual monitor mode?"
date: 2011-01-28
forum: General Help
---

### Post by trpnblies7 on 2011-01-28
I recently hooked my television up to my computer as a second monitor so that I can watch videos on it. However, I don't always want to be in dual monitor mode. I've found that running "gksudo nvidia-settings" allows me to switch between the two modes without restarting X if I change some settings around and click "apply". 

Is there a way I could setup two scripts to handle this process? The main problem I'm encountering is the fact that I change all the settings through the nvidia-settings graphical interface; therefore, I have no idea what's actually happening behind the scenes, so I don't know how to go about putting the two scripts together (what commands to issue, etc.). Could someone help me out with this?

Thank you

---

### Post by mrhhug on 2011-01-29
have you see this?

[http://www.linuxquestions.org/questions/linux-software-2/using-nvidia-settings-from-the-command-line-only-647626/](http://www.linuxquestions.org/questions/linux-software-2/using-nvidia-settings-from-the-command-line-only-647626/)

create a launcher

---

### Post by Krytarik on 2011-01-29
Xrandr manual:
[http://manpages.ubuntu.com/manpages/maverick/en/man1/xrandr.1.html](http://manpages.ubuntu.com/manpages/maverick/en/man1/xrandr.1.html)

Guide for setting monitor modes, you will need this to turn the monitor on again:
[https://wiki.ubuntu.com/X/Config/Resolution](https://wiki.ubuntu.com/X/Config/Resolution)

Thread with a live example regarding a similar intention:
[http://ubuntu-virginia.ubuntuforums.org/showthread.php?p=9885433](http://ubuntu-virginia.ubuntuforums.org/showthread.php?p=9885433)

---

### Post by trpnblies7 on 2011-01-29
> **mrhhug said:**
> have you see this?

[http://www.linuxquestions.org/questions/linux-software-2/using-nvidia-settings-from-the-command-line-only-647626/](http://www.linuxquestions.org/questions/linux-software-2/using-nvidia-settings-from-the-command-line-only-647626/)

create a launcher

I read through that, but I'm not sure how to apply it to my situation. In that thread, the person only has one screen active at a time (either his laptop screen or his external monitor). For me, I will always have my main monitor active, but I'd like to be able to switch between having just my monitor active and having both my monitor and TV active at the same time.

I've looked at the differences between xorg.conf when I'm in single-monitor mode vs dual-monitor mode, but I can't figure out what to change so that I can use xrandr like the person in that thread. I've put the differences in blue below.

Single-monitor xorg.conf:
```
Section "Monitor"
    # HorizSync source: edid, VertRefresh source: edid
    Identifier     "Monitor0"
    VendorName     "Unknown"
[B][COLOR="Blue"]    ModelName      "Acer X223W"
    HorizSync       30.0 - 82.0
    VertRefresh     56.0 - 76.0[/COLOR][/B]
    Option         "DPMS"
EndSection

Section "Device"
    Identifier     "Device0"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "GeForce 8800 GT"
EndSection

Section "Screen"
    Identifier     "Screen0"
    Device         "Device0"
    Monitor        "Monitor0"
    DefaultDepth    24
**    [COLOR="Blue"]Option         "TwinView" "0"[/COLOR]**
    Option         "TwinViewXineramaInfoOrder" "DFP-0"
**   [COLOR="Blue"] Option         "metamodes" "DFP: nvidia-auto-select +0+0"[/COLOR]**
    SubSection     "Display"
        Depth       24
    EndSubSection
EndSection

```

Dual-monitor xorg.conf:
```
Section "Monitor"
    # HorizSync source: edid, VertRefresh source: edid
    Identifier     "Monitor0"
    VendorName     "Unknown"
[B][COLOR="Blue"]    ModelName      "LG Electronics LG TV"
    HorizSync       30.0 - 83.0
    VertRefresh     58.0 - 62.0[/COLOR][/B]
    Option         "DPMS"
EndSection

Section "Device"
    Identifier     "Device0"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "GeForce 8800 GT"
EndSection

Section "Screen"
    Identifier     "Screen0"
    Device         "Device0"
    Monitor        "Monitor0"
    DefaultDepth    24
**[COLOR="Blue"]    Option         "TwinView" "1"[/COLOR]**
    Option         "TwinViewXineramaInfoOrder" "DFP-0"
**[COLOR="Blue"]    Option         "metamodes" "CRT: 1680x1050 +1680+0, DFP: nvidia-auto-select +0+0"[/COLOR]**
    SubSection     "Display"
        Depth       24
    EndSubSection
EndSection
```

Is there a way I could put both options in one xorg.conf file and be able to switch between them?

---

### Post by mrhhug on 2011-01-29
i stole this from here : [http://www.dotkam.com/2007/06/02/switch_between_dual-single_monitor_on_ubuntu_linux/](http://www.dotkam.com/2007/06/02/switch_between_dual-single_monitor_on_ubuntu_linux/)

while in single monitor mode do:
```
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.single
```

get into dual monitor mode by whatever means possible then do 
```
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.dual
```

write the 2 scripts
```
echo "#/bin/sh \
# restart gdm with single monitor support \
sudo cp /etc/X11/xorg.conf.single /etc/X11/xorg.conf; sudo /etc/init.d/gdm restart" > ./singledisplay
```
```
echo "#/bin/sh \
# restart gdm with dual monitor support \
sudo cp /etc/X11/xorg.conf.dual /etc/X11/xorg.conf; sudo /etc/init.d/gdm restart" > ./dualdisplay
```
move the 2 scripts so all you have to do it type the script name
```
sudo mv ./dualdisplay /usr/bin/dualdisplay
```
```
sudo mv ./singledisplay /usr/bin/singledisplay
```
make the both executable
```
sudo chmod +x /usr/bin/singledisplay
```
```
sudo chmod +x /usr/bin/dualdisplay
```

now all you have to do it open a terminal and type "sudo dualdisplay" or "sudo singledisplay" and everything should be automated.
Im sure there is a way to do this with one script instead of 2 and also a launcher but this should make your life a little easier - sorry i didnt have dual displays to test the thing

---

### Post by trpnblies7 on 2011-01-29
That's close to what I'm trying to accomplish, but that method still requires restarting X. I think the xrandr way is what I need to try and figure out, but suited to my setup. Thank you, though. I appreciate the help!

---

### Post by realzippy on 2011-01-29
Have a look at [disper]("http://willem.engen.nl/projects/disper/").
it is made for this purpose.

---

### Post by trpnblies7 on 2011-01-29
> **realzippy said:**
> Have a look at [disper]("http://willem.engen.nl/projects/disper/").
it is made for this purpose.

Thank you! That does *exactly* what I want.

---

