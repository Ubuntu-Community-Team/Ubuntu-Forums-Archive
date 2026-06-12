---
title: "Dual Monitor Setup (Toshiba U500)"
date: 2011-04-07
forum: General Help
---

### Post by FriesWithDatt on 2011-04-07
I've just installed Ubuntu 10.10 on my Toshiba U500 laptop. It has an Intel Family 4 chipset (4500m).

Originally I was able to connect via VGA to an external monitor perfectly fine, resolution was fair. However, now whenever I connect before or after booting both monitors align half off their respective screens and my external has terrible resolution now.

My laptop and external monitor have 1280x800 and 1680x1050 native resolutions respectively. Here's what I get when I run xrandr (unfortunately that's the extent of my terminal skills):

```
[INDENT]Screen 0: minimum 320 x 200, current 2960 x 1050, maximum 8192 x 8192
VGA1 connected 1680x1050+1280+0 (normal left inverted right x axis y axis) 474mm x 296mm
   1680x1050      59.9*+
   1280x1024      75.0     60.0  
   1280x960       60.0  
   1152x864       75.0  
   1024x768       75.1     70.1     60.0  
   832x624        74.6  
   800x600        72.2     75.0     60.3     56.2  
   640x480        72.8     75.0     66.7     60.0  
   720x400        70.1  
LVDS1 connected 1280x800+0+250 (normal left inverted right x axis y axis) 287mm x 180mm
   1280x800       60.0*+
   1024x768       60.0  
   800x600        60.3     56.2  
   640x480        59.9  
HDMI1 disconnected (normal left inverted right x axis y axis)
DP1 disconnected (normal left inverted right x axis y axis)
HDMI2 disconnected (normal left inverted right x axis y axis)
DP2 disconnected (normal left inverted right x axis y axis)
DP3 disconnected (normal left inverted right x axis y axis)
TV1 disconnected (normal left inverted right x axis y axis)

[/INDENT]
```

Any ideas how to fix the screen alignment permanently?

---

