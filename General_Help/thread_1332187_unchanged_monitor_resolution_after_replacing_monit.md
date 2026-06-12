---
title: "unchanged monitor resolution after replacing monitor with better one"
date: 2009-11-20
forum: General Help
---

### Post by Chily123 on 2009-11-20
I installed ubuntu 9.04 with a monitor. The resolution if it was 1280x1024. After replacing it with a bigger 22 inch 1680x1050 monitor, i wasn't able to change the resolution to a higher one (I know the graphics card supports it, because it works under windows).
In thought to modify my xorg.conf by hand, but this didn't help. It seems like it is ignored. Any help would be greatly apreciated.

Here my actual /etc/X11/xorg.conf

Section "Device"
    Identifier    "Configured Video Device"
EndSection

Section "Monitor"
   Identifier  "HANNS G Hi 221D"
#    Identifier    "BELINEA 101751"
    Horizsync    30-80
    Vertrefresh    56-76
EndSection

Section "Screen"
    Identifier    "Default Screen"
   Monitor     "HANNS G Hi 221D"
#    Monitor        "BELINEA 101751"
    Device        "Configured Video Device"
    Defaultdepth    24
    SubSection    "Display"
        Depth    24
      Modes "1680x1050" "1280x1024" "1024x768" "800x600"
#        Modes    "1280x1024"
    EndSubSection
EndSection

---

### Post by P4man on 2009-11-20
you didnt change these values:
Horizsync 30-80
Vertrefresh 56-76

which define what the monitor is capable off. Try commenting them out, it will probably autodetect. If not, change those values to match your monitor specifications

---

### Post by Chily123 on 2009-11-20
Much thx for help. but commenting the hsync and vsync out changed my resolution to 800x600. Unfortunately i do not find the sync-frequencies of my monitor. What should i do ?

---

### Post by P4man on 2009-11-20
From your manufacturer website this seems to be your monitor;s settings:

```
Horizsync 24-83
Vertrefresh 56-76
```

If that doesnt solve it, try adding a modeline:

```
Section "Monitor"
   Identifier "HANNS G Hi 221D"
   # Identifier "BELINEA 101751"
[COLOR="Red"]   Horizsync 24-83
   Vertrefresh 56-76
   Modeline "1680x1050_60.00"  146.25  1680 1784 1960 2240  1050 1053 1059 1089 -hsync +vsync[/COLOR]
EndSection
```

---

### Post by P4man on 2009-11-20
If that still doenst work, try this in a terminal:

```
sudo rm ~/.config/monitors.xml
```

---

### Post by Chily123 on 2009-11-20
finally solved it. 

I first noticed the resolutions shown on the monitor in windows and then tryed to create the range out of it. But this didn't help.

Finally i tryied a closed source driver. I istalled this  nvidia driver and there the problem was solved.  Too bad it's closed source :/ but at least it works now.


Edit: Thx so much for your help. I'll try it, when i have more time. (page bookmarked ^^)

---

