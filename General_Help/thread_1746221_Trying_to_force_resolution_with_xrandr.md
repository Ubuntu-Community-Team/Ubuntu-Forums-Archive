---
title: "Trying to force resolution with xrandr"
date: 2011-05-01
forum: General Help
---

### Post by Arsic on 2011-05-01
Can anyone tell me what's wrong?
```
$ xrandr
Screen 0: minimum 320 x 200, current 1024 x 600, maximum 4096 x 4096
VGA1 disconnected (normal left inverted right x axis y axis)
LVDS1 connected 1024x600+0+0 (normal left inverted right x axis y axis) 220mm x 129mm panning 1024x600+0+0
   1024x600       60.0*+
   800x600        60.3     56.2  
   640x480        59.9  
$ cvt 1024 768
# 1024x768 59.92 Hz (CVT 0.79M3) hsync: 47.82 kHz; pclk: 63.50 MHz
Modeline "1024x768_60.00"   63.50  1024 1072 1176 1328  768 771 775 798 -hsync +vsync
$ xrandr --newmode "1024x768_60.00" 70.00 1024 1072 1176 1328 768 771 775 798 -hsync +vsync
$ xrandr --addmode LVDS1 1024x768_60.00
X Error of failed request:  BadMatch (invalid parameter attributes)
  Major opcode of failed request:  150 (RANDR)
  Minor opcode of failed request:  18 (RRAddOutputMode)
  Serial number of failed request:  25
  Current serial number in output stream:  26

```

Aside from this ASUS 1015PEM netbook's Intel GMA 3150 only supporting resolutions up to 1024x600, I hope that's not why.

I got this to force 1920x1080 on VGA1 when connected to a monitor, but it won't do it for LVDS1 despite telling me that it's maximum is 4096x4096 on Screen 0.

---

### Post by Argentino on 2011-05-03
Hi,

You are giving it info it does not need. do this:

```

$ xrandr --newmode name 70.00 1024 1072 1176 1328 768 771 775 798

```
then

```

$ xrandr --addmode LVDS1 name

```

all done, you can replace "name" with whatever you want to call the new mode.

Hope that helps

---

