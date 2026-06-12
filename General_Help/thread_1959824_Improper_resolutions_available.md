---
title: "Improper resolutions available"
date: 2012-04-16
forum: General Help
---

### Post by ucal on 2012-04-16
Hi all, I went to sleep with a high resolution screen and no care in the world, and I woke up with an ugly 1024X768 resolution plaster on my monitor, and that's the highest option in the default display manager.  I have no idea what happened while I was sleeping to cause this.  

xrandr gives an output of:
```
Screen 0: minimum 320 x 200, current 1024 x 768, maximum 8192 x 8192
VGA1 connected 1024x768+0+0 (normal left inverted right x axis y axis) 0mm x 0mm
   1024x768       60.0* 
   800x600        60.3     56.2  
   848x480        60.0  
   640x480        59.9  
HDMI1 disconnected (normal left inverted right x axis y axis)
DP1 disconnected (normal left inverted right x axis y axis)
HDMI2 disconnected (normal left inverted right x axis y axis)
HDMI3 disconnected (normal left inverted right x axis y axis)
DP2 disconnected (normal left inverted right x axis y axis)
DP3 disconnected (normal left inverted right x axis y axis)

```

So it looked like my X just stopped detecting my monitor's appropriate values for some reason.  Any idea how to fix this?

---

### Post by ucal on 2012-04-16
Somehow, unplugging everything from the display, and rebooting the computer first without a monitor, and then with the monitor worked to restore my options.  Still, I'd like to know why this happened if some kind soul would be able to explain it.

---

