---
title: "Resolution can't be set correctly"
date: 2010-03-17
forum: General Help
---

### Post by Kenji2 on 2010-03-17
Hello

I just installed ubuntu 9.10 (latest version + updates) on my computer. I am new to the linux OS.

Ok let's get to the problem. I have a 1366x768 resolution monitor with a maximum vertical frequency of 60 hz. This worked well on windows. As I've already read in the internet, this can rise problems on Ubuntu. The monitor is connected through a switchbox, so it doesn't get recognised. Even if it's hooked up directly (Ubuntu recognises it) I can't choose the correct resolution.

Currently I can't use another graphics driver than the generic one. The screen stays black ("wrong vertical frequency" displayed on LCD Monitor) if I use another driver. I'd like to use the proprietary ATI/AMD fglrx driver.

I edited the xorg.conf file, but I was unable to get the right resolution. It seems to be outdated on Ubuntu 9.10. After that fail, I searched for alternatives and ended up with a file called

45custom_xrandr-settings

in the "Xsession.d" folder. I'm using the following contents:

```

xrandr --newmode "1366x768_60.00" 85.86  1368 1440 1584 1800  768 769 772 795  -HSync +Vsync
xrandr --addmode VGA-0 "1366x768_60.00"
xrandr --output VGA-0 --mode 1366x768_60.00
```But the monitor still complains that it's the wrong vertical frequency when I use the fglrx driver. The generic driver uses another resolution than the specified one (as always) and gives me a blurry picture on the screen. I have also tried other modelines, Ubuntu just doesn't seem to be able to display 1366x768@60hz.

I'd be glad if you could help me there.

yours
Kenji2

---

### Post by drewsus on 2010-03-17
could it be as simple as using a different refresh rate?
(59.9)

Also, exactly, what monitor do you have?

dRewsus

---

### Post by Kenji2 on 2010-03-17
> **drewsus said:**
> could it be as simple as using a different refresh rate?
(59.9)

No, I've tried it.

> **drewsus said:**
> 
Also, exactly, what monitor do you have?


Its name is Q19 Cinema, 18.5'' widescreen TFT Monitor, a brand of quanmax.
Don't ask me where it's from - it's small and ugly and has a bad quality, but I'd like to get at least the resolution correct :)

---

### Post by drewsus on 2010-03-17
So I tried to find a manual to see the various resolution options, but that seems to be a very rare monitor ha

Anyway, how do you know that the resolution is supposed to be 1366x768?

Also, can you post the output of:
```
xrandr -q
```
please

---

### Post by patchwork on 2010-03-17
> Ubuntu just doesn't seem to be able to display 1366x768@60hz.

Ubuntu shows 1366x768@ 60Hz just fine (it's what I'm using).  The problem is more likely to be in the modeline or problems with the driver.

You can check your modeline with
```
cvt 1366 768
```

Also, the xorg.conf will be read if it is present (though most computers do not require one anymore).  You can create one specific to your computer, and only add the sections (and options) you need (i.e Section "Device", Driver "fglrx", Section "Monitor", VertRefresh, HorizSync, etc)

Just remember that every Section needs an EndSection

The man page
```
man xorg.conf
```will give you more details.

Also, I haven't heard much good said about the fglrx driver....many people avoid it like the plague, although I have no experience with it myself (using nvidia)

---

### Post by drewsus on 2010-03-18
I don't know why but when I do: 
```
gtf 1366 768 59.9
//OR
cvt 1366 768

```
I get 136_***8***_x768

---

### Post by Kenji2 on 2010-03-18
> **drewsus said:**
> So I tried to find a manual to see the various resolution options, but that seems to be a very rare monitor ha

Yes, it is in fact a really rare monitor. I searched for specific ubuntu resolution problems with this monitor and found nothing.

> **drewsus said:**
> Anyway, how do you know that the resolution is supposed to be 1366x768?

I have a manual and a magazine of the computer shop.
The manual says 1360x768, the magazine article says  1366x768 and the modeline generator makes 1368x768 (as already mentioned in the post above).

However, I think I used a resolution of 1366x768 on windows and it fitted perfectly.

> **drewsus said:**
> Also, can you post the output of:
```
xrandr -q
```please

Yes, that's the output:
```

Screen 0: minimum 320 x 200, current 1360 x 768, maximum 1360 x 1360
VGA-0 connected 1360x768+0+0 (normal left inverted right x axis y axis) 0mm x 0mm
   1360x768       59.8* 
   1152x864       60.0  
   1024x768       60.0  
   800x600        60.3  
   640x480        59.9  
   1366x768_60.00   41.9  
HDMI-0 disconnected (normal left inverted right x axis y axis)
DVI-0 disconnected (normal left inverted right x axis y axis)
```Please note that the picture really _isn't_ 1360x768, it's 1280x768 (my monitor shows it)

I already edited xorg.conf file many times. I tried a lot of different modelines and settings. These xrandr commands do the same. Both ways don't work.
I need the fglrx driver to activate visual effects. Another problem is that firefox crashes when I make flash applications (youtube) fullscreen. I hope these Problems will get solved if fglrx works.

---

### Post by Kenji2 on 2010-03-18
I have tried to solve the problem by reinstalling the ati driver and adding an xorg.conf.
It still doesn't work. My screen still complains that the VertRefresh is too fast (75hz). My graphic driver obviously doesn't do what I write in the xorg.conf file, as you can see here:
```
Section "ServerLayout"
    Identifier     "aticonfig Layout"
    Screen      0  "aticonfig-Screen[0]-0" 0 0
EndSection

Section "Files"
EndSection

Section "Module"
EndSection

Section "Monitor"
    Identifier   "aticonfig-Monitor[0]-0"
    HorizSync    50.0 - 60.0
    VertRefresh  50.0 - 60.0
    Modeline "1360x768_60.00"  84.72  1360 1424 1568 1776  768 769 772 795  -HSync +Vsync
    Option        "VendorName" "ATI Proprietary Driver"
    Option        "ModelName" "Generic Autodetecting Monitor"
    Option        "DPMS" "true"
EndSection

Section "Device"
    Identifier  "aticonfig-Device[0]-0"
    Driver      "fglrx"
    Option        "EnableRandR12" "false"
    BusID       "PCI:1:0:0"
EndSection

Section "Screen"
    Identifier "aticonfig-Screen[0]-0"
    Device     "aticonfig-Device[0]-0"
    Monitor    "aticonfig-Monitor[0]-0"
    DefaultDepth     24
    SubSection "Display"
        Viewport   0 0
        Depth     24
        Modes    "1360x768_60.00"
    EndSubSection
EndSection

```

---

### Post by Kenji2 on 2010-03-19
Hello

It works now. The problem was the VGA-cable. It was an old one with a lot of pins missing. This didn't allow Ubuntu and the drivers to synchronize resolution and frequency. I'm using another VGA-cable now and everything works fine.

Thank you for your help and suggestions.

Problem solved.

yours
Kenji

---

