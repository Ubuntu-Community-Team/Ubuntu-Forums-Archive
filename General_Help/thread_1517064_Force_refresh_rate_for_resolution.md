---
title: "Force refresh rate for resolution"
date: 2010-06-24
forum: General Help
---

### Post by levo_smetalo on 2010-06-24
I have kinda strange problem with graphics card and monitor. I have nVidia 7600 GT and Samsung 1280x1024 LCD display. X uses nVidia proprietary driver. Desktop environment is Gnome but I use krusader so kde-desktop is also installed In games that require 800x600 mode bottom of the screen gets cut off, like the resolution is 800x450 so bottom 150px are not visible.

my xrandr out:
```

Screen 0: minimum 320 x 240, current 1280 x 1024, maximum 1280 x 1024
default connected 1280x1024+0+0 0mm x 0mm
   1280x1024      50.0*    51.0  
   1280x960       52.0  
   1152x864       53.0     54.0     55.0     56.0  
   1024x768       57.0     58.0     59.0  
   960x600        60.0  
   960x540        61.0  
   840x525        62.0     63.0     64.0  
   832x624        65.0  
   800x600        66.0     67.0     68.0     69.0     70.0     71.0  
   800x512        72.0  
   720x450        73.0  
   680x384        74.0     75.0  
   640x512        76.0     77.0  
   640x480        78.0     79.0     80.0     81.0     82.0     83.0  
   576x432        84.0     85.0     86.0     87.0  
   512x384        88.0     89.0     90.0  
   416x312        91.0  
   400x300        92.0     93.0     94.0     95.0  
   320x240        96.0     97.0     98.0  

```

cvt out for "cvt 800 600"

```
# 800x600 59.86 Hz (CVT 0.48M3) hsync: 37.35 kHz; pclk: 38.25 MHz
Modeline "800x600_60.00"   38.25  800 832 912 1024  600 603 607 624 -hsync +vsync


```

Some time ago, on Karmic I managed to fix this issue by removing 66.0 refresh rate for 800x600 resolution (or was it both 66 and 67 :oops:). Once I did that, all games working in 800x600 were displayed correctly. However, since I installed Lucid the issue is back and I can't seem to remember how did I fix that issue before. 
Does anyone know exact steps to force 800x600 (or any other resolution) to use specific refresh rate?

---

### Post by levo_smetalo on 2010-06-25
I found the solution. I added following line to [Device] section of xorg.conf

```
    Option "ModeValidation" "NoXServerModes"
```

and voila! my 800x600 mode works normally now.

---

