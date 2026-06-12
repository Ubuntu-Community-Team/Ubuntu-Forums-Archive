---
title: "Monitor doesn't show menu bars/panels"
date: 2011-07-15
forum: General Help
---

### Post by briealeida on 2011-07-15
Hello!

I've got a fresh install of Natty on my Dell Studio 17 laptop. The screen on the laptop doesn't work so I have it plugged into my Panasonic TV with an HDMI cable. The only problem is that the TV is not showing the outer edges of my desktop. So, I can't see the "Applications" menu, for example, or the button to click to Logout. I've messed with every setting available on the TV and nothing has helped.

Can anyone provide any advice? I've started messing around with xrandr but it doesn't seem to help. Here is the output of 'xrandr':

Screen 0: minimum 320 x 200, current 3360 x 1207, maximum 8192 x 8192
LVDS1 connected 1440x900+1920+0 (normal left inverted right x axis y axis) 367mm x 229mm
   1440x900       60.1*+   59.9  
   1360x768       59.8     60.0  
   1152x864       60.0  
   1024x768       60.0  
   800x600        60.3     56.2  
   640x480        59.9  
VGA1 disconnected (normal left inverted right x axis y axis)
HDMI1 connected 1920x1080+0+127 (normal left inverted right x axis y axis) 698mm x 392mm
   1920x1080      60.0*+
   1280x720       60.0  
DP1 disconnected (normal left inverted right x axis y axis)
DP2 disconnected (normal left inverted right x axis y axis)

---

### Post by briealeida on 2011-07-15
Got it! Both monitors were turned on. I turned off the Laptop and selected the television as the only monitor turned on. As I couldn't open GNOME Display Properties without seeing the panels on the laptop, I had to do:

  ls /usr/bin/ | grep gnome

And try a few that sounded good. The one to use is /usr/bin/gnome-display-properties

---

