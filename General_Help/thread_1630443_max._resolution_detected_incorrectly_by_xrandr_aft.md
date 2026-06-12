---
title: "max. resolution detected incorrectly by xrandr after connecting to external  monitor"
date: 2010-11-25
forum: General Help
---

### Post by Rockroehre on 2010-11-25
Hi everyone,

first my setup:
Thinkpad R500
installed: maverick, lucid, Windows7 (each on its on partition)
VGA compatible controller: ATI Technologies Inc Mobility Radeon HD 3400 Series
driver: ATI/AMD proprietary FGLRX graphics driver

Yesterday I was logged into maverick and connected to an external monitor via RGB. To show my desktop on the monitor, I chose System > Preferences > Monitors. The monitor was detected, it was suggested I adjust my resolution settings, I accepted. I could see my login screen on the external monitor, but unfortunately the external monitor would turn black after logging in, so I repeated the adjustment procedure a few more times. It wouldn't help, so I gave up. To disconnect, I simply unplugged the RGB cable.

When I wanted to change the resolution settings on my laptop back to what they used to be (System > Preferences > Monitors > Resolution), I found that maximum resolution I could choose was 1400x1050, although I used to have it set to 1680x1050.  I've been using maverick on my Thinkpad since the release and I've never had problems with my resolution settings. I googled for explanations, but didn't really find anything. Has anyone experienced the same?

Here's what xrandr says:
```

...@...:~$ xrandr
Screen 0: minimum 320 x 200, current 1440 x 900, maximum 1440 x 1440
LVDS connected 1440x900+0+0 (normal left inverted right x axis y axis) 331mm x 207mm
   1400x1050      60.0 +   50.0  
   1280x1024      60.0 +   50.0  
   1440x900       59.9*+   50.0  
   1280x960       60.0 +   50.0  
   1280x800       60.0 +   50.0  
   1152x864       60.0 +   50.0  
   1280x768       59.9 +   50.0  
   1280x720       60.0 +   50.0  
   1024x768       60.0 +   50.0  
   1024x600       60.4 +   50.0  
   800x600        60.3 +   50.0  
   800x480        60.0 +   50.0  
   720x480        60.0 +   50.0  
   640x480        60.0 +   50.0  
DFP1 disconnected (normal left inverted right x axis y axis)
DFP2 disconnected (normal left inverted right x axis y axis)
CRT1 disconnected (normal left inverted right x axis y axis)
```Here's what xrandr says when I log into lucid (same laptop, same screen!)
```

...@...:~$ xrandr
Screen 0: minimum 320 x 200, current 1680 x 1050, maximum 2960 x 1050
LVDS connected 1680x1050+0+0 (normal left inverted right x axis y axis) 0mm x 0mm
   1680x1050      60.0*+   50.0  
   1400x1050      60.0 +
   1280x1024      60.0 +
   1440x900       59.9 +
   1280x960       60.0 +
   1280x800       60.0 +
   1152x864       60.0 +
   1280x768       59.9 +
   1280x720       60.0 +   50.0  
   1024x768       60.0 +
   1024x600       60.4 +
   800x600        60.3 +
   800x480        60.0 +
   720x480        60.0 +
   640x480        60.0 +
DFP1 disconnected (normal left inverted right x axis y axis)
DFP_EXTTMDS disconnected (normal left inverted right x axis y axis)
CRT1 disconnected (normal left inverted right x axis y axis)
```Any ideas?

Thanks in advance!

---

### Post by itang sanjana on 2010-11-25
Yup, this is common problem. Configuring xorg.conf seems the only solution to me. Here you can found how this is done [https://wiki.ubuntu.com/X/Config/Resolution](https://wiki.ubuntu.com/X/Config/Resolution) HTH.

---

### Post by Rockroehre on 2010-11-25
I don't have an xorg.conf file. I could obviously create one, but my understanding was that, in maverick, things are supposed to be dealt with using xrandr instead of xorg.conf. Is that wrong?

As I see it, the problem lies somewhere in the difference between these two lines:
maverick:
```

LVDS connected 1440x900+0+0
 
```

lucid:
```

LVDS connected 1680x1050+0+0

```

---

### Post by itang sanjana on 2010-11-25
You're right, since 9.10 Ubuntu no longer use xorg.conf, but still if there is xorg.conf exist in /etc/X11, Ubuntu will use it. AFAIK xrandr is not permanent. That's mean you should run xrandr every time you login to X Window or you can use xorg.conf to set your desired resolution automagicaly .. CMIIW

---

### Post by Rockroehre on 2010-11-25
Would it be a bad idea to just add the 1680x1050 mode via xrandr as described here?
[https://wiki.ubuntu.com/X/Config/Resolution#Adding%20undetected%20resolutions](https://wiki.ubuntu.com/X/Config/Resolution#Adding%20undetected%20resolutions)

I'm not sure it would work though, since the new mode would exceed the maximum resolution detected by xrandr (1440 x 1440). But how can I change what xrandr detects as the maximum resolution?

---

### Post by Rockroehre on 2010-11-25
Sorry, I think our posts just overlapped. I'll try by setting up an xorg.conf file.

---

### Post by itang sanjana on 2010-11-25
Use cvt, cvt <desired resolution> i.e. ```
cvt 1680 1050
# 1680x1050 59.95 Hz (CVT 1.76MA) hsync: 65.29 kHz; pclk: 146.25 MHz
Modeline "1680x1050_60.00"  146.25  1680 1784 1960 2240  1050 1053 1059 1089 -hsync +vsync
``` then use the modeline result as describe on the wiki ..

---

### Post by itang sanjana on 2010-11-25
> **Rockroehre said:**
> Sorry, I think our posts just overlapped. I'll try by setting up an xorg.conf file.
you should exit from X window first ```
Ctrl+Alt+F1
``` than stop the DM login manager than run ```
sudo X -configure
``` HTH

---

### Post by Rockroehre on 2010-11-25
I finally got it fixed.

Shame on me... I made a mistake when looking for the xorg.conf file - I actually do have one. Turns out I even had two:

xorg.conf
```

Section "Screen"
        Identifier      "Default Screen"
        DefaultDepth    24
        SubSection "Display"
                     Virtual 3360 1050
        EndSubSection
EndSection

Section "Module"
        Load    "glx"
EndSection

Section "Device"
        Identifier      "Default Device"
        Driver  "fglrx"
EndSection

/etc/X11/xorg.conf (END) 

```xorg.conf.20101124173335
```

Section "Screen"
        Identifier      "Default Screen"
        DefaultDepth    24
EndSection

Section "Module"
        Load    "glx"
EndSection

Section "Device"
        Identifier      "Default Device"
        Driver  "fglrx"
EndSection

xorg.conf.20101124173335 (END)

```20101124173335 is the date and time I connected the external monitor, so I just deleted the SubSection "Display" part from the xorg.conf file, restarted and suddenly the 1680x1050 option was available again in System > Preferences > Monitors > Resolution. I chose it and everything went back to normal. Halleluja. ;)

Thanks so much for your help and sorry for my mishap!

---

