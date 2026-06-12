---
title: "xrandr not working"
date: 2011-11-30
forum: General Help
---

### Post by LewisKolb on 2011-11-30
hello all,
i recently just installed Xubuntu, first time ive even seen a linux OS so bear with me.
im trying to force a 1920x1080 resolution at 60hz and to no prevail.

this is what i punched into the terminal.

lewis@LewisUbuntu:~$ cvt 1920 1080
# 1920x1080 59.96 Hz (CVT 2.07M9) hsync: 67.16 kHz; pclk: 173.00 MHz
Modeline "1920x1080_60.00"  173.00  1920 2048 2248 2576  1080 1083 1088 1120 -hsync +vsync
lewis@LewisUbuntu:~$ xrandr --newmode "1920x1080_60.00"  173.00  1920 2048 2248 2576  1080 1083 1088 1120 -hsync +vsync
[SIZE=2]**xrandr: Failed to get size of gamma for output default**[/SIZE]

I followed a tutorial word for word and this is what happened, Am i doing something wrong?

thanks.

---

