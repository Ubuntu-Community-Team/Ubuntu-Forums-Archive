---
title: "ubuntu doens't recognize my monitor's resolution"
date: 2010-08-01
forum: General Help
---

### Post by wachrno on 2010-08-01
Hi,

I'm not sure if this is the right category to ask for help but here it goes:

I have a laptop with ubuntu 10.04x64 and i have bought recently a samsung xl2370 which has a max resolution of 1080p but the maximum resolution my laptop recognizes is 1440x900 is there any way to solve this?
Thanks in advance

---

### Post by wachrno on 2010-08-01
help plz? did anyone else had the same problem but in a different monitor?

---

### Post by sblanzio on 2010-10-08
did you solve this problem? I got the same issue.

tyvm

---

### Post by killerrex on 2010-10-31
Maybe is a little too late, but I have found a solution for this monitor.
The problem seems to be an incorrect EDID in the monitor and even when I have contacted the Samsung support they have no idea of how I can fix the problem.
So finally I have found in the VESA standard the way to calculate the modeline parameters with the info of the manual (it does not work with the cvt output)
The modeline is:
```

# Calculated for 1920x1080p with (see manual chapter 3-2):
#  Pixel Clock 148.5 MHz
#  Horizontal Freq: 67.5 kHz
#  Vert Freq: 60.0 Hz
ModeLine "1920x1080"  148.50  1920 2028 2060 2200  1080 1083 1088 1125 +hsync +vsync

```To use it in a new system without an xorg.conf file you can add the next code to the beggining of the file (after the first comments):
/etc/gdm/Init/Default
```

# Add the new mode to DVI-0
xrandr --newmode "1920x1080"  148.50  1920 2028 2060 2200  1080 1083 1088 1125 +hsync +vsync
xrandr --addmode DVI-0 "1920x1080"
xrandr --output DVI-0 --mode "1920x1080"

```

Check before that the frequencies of your version are the same before using the modeline...

---

