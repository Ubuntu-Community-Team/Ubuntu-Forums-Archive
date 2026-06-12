---
title: "Laptop Display problem...Please help!"
date: 2012-02-17
forum: General Help
---

### Post by belmont52 on 2012-02-17
Hi all, 

I have a dell laptop running 11.10 and I have benn having a problem with my displays when I use my docking station at work. When I am at home or moving around the office, I just use the laptop screen. However, when I am in my office, I have 2 monitors attached to a docking station and I plug my laptop into that and close the lid. I can set all the display settings up so that the screens work like I want them to but if I take it out of the station and plug it back in, the screen resolutions go crazy and I get different results every time. the only workaround i have found is to restart the computer while on the station but this is very inefficient for me. I suppose I am looking for a display profile switcher that detects whether or not I have the docking station connected and switches accordingly. I should also note that the 2 monitors have the same resolution and size but the laptop screen is different. Any help with this problem would be greatly appreciated!

Thanks in advance

---

### Post by Paddy Landau on 2012-02-18
The only two things I can suggest are:

[LIST]
[*]Open your Monitors app before disconnecting and disable the attached monitor.
[/LIST]

[LIST]
[*]Or, log out (instead of rebooting) before disconnecting. Although it's a nuisance, it's quicker than rebooting.
[/LIST]

---

### Post by belmont52 on 2012-03-06
I will try that when I go into work tomorrow, thank you!

---

### Post by bundacia on 2012-11-27
I'm having the same issue with 12.10 on a DELL Latitude E5400. Has anyone found a better solution? Logging out every time I undock seems like a hassle.

---

### Post by bundacia on 2012-11-27
Ok, I think I'm a bit closer. I found you can use xrandr to change which monitors are used manually. This thread was helpful: [http://ubuntuforums.org/showthread.php?t=1590782](http://ubuntuforums.org/showthread.php?t=1590782)

Running xrandr without any options will display your setup:

> 
$ xrandr
Screen 0: minimum 320 x 200, current 2560 x 1024, maximum 8192 x 8192
LVDS1 connected (normal left inverted right x axis y axis)
   1280x800       60.0 +   40.0  
   1024x768       60.0  
   800x600        60.3     56.2  
   640x480        59.9  
VGA1 connected 1280x1024+0+0 (normal left inverted right x axis y axis) 338mm x 270mm
   1280x1024      60.0*+   75.0  
   1280x960       60.0  
   1280x800       74.9     59.8  
   1152x864       75.0  
   1280x768       74.9     59.9  
   1024x768       75.1     70.1     60.0  
   1024x576       60.0  
   800x600        72.2     75.0     60.3     56.2  
   848x480        60.0  
   640x480        72.8     75.0     60.0  
   720x400        70.1  
HDMI1 disconnected (normal left inverted right x axis y axis)
DP1 disconnected (normal left inverted right x axis y axis)
HDMI2 connected 1280x1024+1280+0 (normal left inverted right x axis y axis) 338mm x 270mm
   1280x1024      60.0*+   75.0  
   1280x960       60.0  
   1280x800       74.9     59.9  
   1152x864       75.0  
   1280x768       74.9     60.0  
   1024x768       75.1     70.1     60.0  
   1024x576       60.0  
   800x600        72.2     75.0     60.3     56.2  
   848x480        60.0  
   640x480        72.8     75.0     60.0  
   720x400        70.1  
DP2 disconnected (normal left inverted right x axis y axis)
DP3 disconnected (normal left inverted right x axis y axis)
TV1 unknown connection (normal left inverted right x axis y axis)
   848x480        59.9 +
   640x480        59.9 +
   1024x768       59.9  
   800x600        59.9  


VGA1 and HDMI2 are my external monitors connected through my dock, and LVDS1 is the laptop screen. Basiacally I've set up 2 aliases to change between my docked and undocked setup:

```

alias dock='xrandr --output LVDS1 --off; xrandr --output VGA1 --auto --left-of HDMI2 --output HDMI2 --auto'
alias undock='xrandr --output VGA1 --off --output HDMI2 --off; xrandr --output LVDS1 --auto'
```

This seems to work ok, although there's a lot of flashing and blinking at first when I run these commands.

---

