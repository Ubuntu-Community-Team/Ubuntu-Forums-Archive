---
title: "How do I set my external monitor's refresh higher than 60hz?"
date: 2012-09-18
forum: General Help
---

### Post by agekara on 2012-09-18
Hello.
I am a Mac user who has recently installed Ubuntu on a partition to run alongside Mac OSX.
In addition to my Macbook Pro monitor, I also have a Samsung Syncmaster 753df CRT as an external display, connected via mini VGA cable. 

When I run OSX, I can get this monitor to run at 800x600 and ~100hz.

However, when running ubuntu, the monitor seems locked at 60hz. And even when I attempt to use xrandr to increase the refresh rate, it still visibly runs at 60hz. Meanwhile the xrandr command returns this:
```
Screen 0: minimum 320 x 200, current 1289 x 1400, maximum 8192 x 8192
LVDS-1 connected 1280x800+9+0 (normal left inverted right x axis y axis) 286mm x 179mm
   1280x800       60.2*+
   1024x768       59.9  
   800x600        59.9  
   640x480        59.4  
   720x400        59.6  
   640x400        60.0  
   640x350        59.8  
DP-1 connected 800x600+0+800 (normal left inverted right x axis y axis) 312mm x 234mm
   1024x768       85.0 +   75.1     70.1     60.0     43.5  
   1280x1024      60.0  
   1152x864       75.0  
   832x624        74.6  
   800x600        85.1*    72.2     75.0     60.3     56.2  
   640x480        85.0     72.8     75.0     66.7     60.0  
   720x400        87.8     70.1  

```DP-1 being the external monitor in question. It shows that 85.1hz is the selected rate, but the screen is clearly only running at 60, the default.

I have searched endlessly (on google and this forum) for solutions to this problem, but none of them have worked for me so far. Please help!!

---

### Post by jerrrys on 2012-09-19
If its any help, I got a few hits [here]("http://ubuntuforums.org/change%20refresh%20rate%20to%20100%20hz%20ubuntu%2012.04")

---

