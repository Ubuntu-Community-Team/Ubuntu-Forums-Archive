---
title: "adding undetected screen resolution with xrandr in lubuntu"
date: 2012-05-22
forum: General Help
---

### Post by Tjampman on 2012-05-22
Hi
I am having some troubles changing the screen resolution in lubuntu.

It is an old destop pc, with a nvidia 5900 gfx, and as far as I know that is not supported in the newest nvidia drivers for ubuntu 12.04 (something to do with X, I believe) so I am using the nouveau driver that lubuntu came with.
My current resolution is 1024*768 which screws up the aspect ratio on my 16*9 full HD monitor.

Therefor I would very much like to change the resolution to 1366*768.

Here is the output from xrandr
```
ole@all-my-base:~$ xrandr
Screen 0: minimum 320 x 200, current 1024 x 768, maximum 4096 x 4096
VGA-1 connected 1024x768+0+0 (normal left inverted right x axis y axis) 0mm x 0mm
   1024x768       60.0* 
   800x600        60.3     56.2  
   848x480        60.0  
   640x480        59.9  
DVI-I-1 disconnected (normal left inverted right x axis y axis)
TV-1 disconnected (normal left inverted right x axis y axis)

```
it says that max resolution is 4096*4096 so I'm assuming it should be posible to change.

I tried following this guide: [https://wiki.ubuntu.com/X/Config/Resolution#Adding_undetected_resolutions](https://wiki.ubuntu.com/X/Config/Resolution#Adding_undetected_resolutions)
With the following result:
```


ole@all-my-base:~$ cvt 1366 768 60
# 1368x768 59.88 Hz (CVT) hsync: 47.79 kHz; pclk: 85.25 MHz
Modeline "1368x768_60.00"   85.25  1368 1440 1576 1784  768 771 781 798 -hsync +vsync
ole@all-my-base:~$ xrandr --newmode "1368x768_60.00"   85.25  1368 1440 1576 1784  768 771 781 798 -hsync +vsync

ole@all-my-base:~$ xrandr --addmode VGA-1 1366x768
xrandr: cannot find mode "1366x768"
ole@all-my-base:~$ xrandr
Screen 0: minimum 320 x 200, current 1024 x 768, maximum 4096 x 4096
VGA-1 connected 1024x768+0+0 (normal left inverted right x axis y axis) 0mm x 0mm
   1024x768       60.0* 
   800x600        60.3     56.2  
   848x480        60.0  
   640x480        59.9  
DVI-I-1 disconnected (normal left inverted right x axis y axis)
TV-1 disconnected (normal left inverted right x axis y axis)
  1368x768_60.00 (0x1ac)   85.2MHz
        h: width  1368 start 1440 end 1576 total 1784 skew    0 clock   47.8KHz
        v: height  768 start  771 end  781 total  798           clock   59.9Hz

```

what am I doing wrong? And how can I fix it.
thanks in advance

---

### Post by efflandt on 2012-05-22
man xrandr

When you add a mode, you need to add the --newmode first before you can --addmode.  For some reason there is no 1366 mode in Linux, but 1360x768 should work.

```
**cvt 1360 768**
# 1360x768 59.80 Hz (CVT) hsync: 47.72 kHz; pclk: 84.75 MHz
Modeline "1360x768_60.00"   84.75  1360 1432 1568 1776  768 771 781 798 -hsync +vsync

xrandr --newmode "1360x768_60.00"   84.75  1360 1432 1568 1776  768 771 781 798 -hsync +vsync
xrandr --addmode VGA-1 1360x768_60
xrandr --output VGA-1 --mode 1360x768_60
```Some wide screen monitors or HDTVs might auto sync to that, or there may be some menu setting in the monitor to either auto sync or manually adjust size and position to fill the screen.  I used similar xrandr commands in a script for connecting an old laptop with legacy (old) ATI to display VGA to HDTV, except the VGA device numbers for that were slightly different (VGA-0 instead of VGA-1).  Although, I also included another xrandr command to turn the laptop display off.

---

