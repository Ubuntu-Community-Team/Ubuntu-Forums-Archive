---
title: "destroyes mode lines by plugging external screen"
date: 2009-11-08
forum: General Help
---

### Post by gaboro on 2009-11-08
hiya,

i have a samsung x20 laptop with ati x700 and a screen with a resolution of 1400x1050. it works properly under karmic koala. if i fire xrandr it says:  
[FONT="Courier New"]LVDS connected 1400x1050+0+0 (normal left inverted right x axis y axis) 0mm x 0mm
   1400x1050      60.2*+
   1280x1024      59.9     60.0  
   1280x960       60.0     59.9  
   1280x854       59.9  
   1360x768       59.8  
   1280x800       59.8  
   1152x864       60.0  
   1280x720       59.9  
   1152x768       59.8  
   1024x768       60.0     59.9  
   800x600        60.3     59.9  
   640x480        59.9     59.4  [/FONT]
if i plug an external monitor that has a lower resolution (1280x1024), the modes of the laptop screen will be changed, too: 
[FONT="Courier New"]LVDS connected 1400x1050+0+0 (normal left inverted right x axis y axis) 376mm x 301mm
   1280x1024      60.0 +   75.0     59.9     60.0  
   1280x960       59.9  
   1280x854       59.9  
   1280x800       59.8  
   1152x864       75.0  
   1280x720       59.9  
   1152x768       59.8  
   1024x768       75.0     70.1     60.0     59.9  
   832x624        74.6  
   800x600        72.2     75.0     60.3     59.9     56.2  
   640x480        75.0     72.8     66.7     59.9     59.4  
   720x400        70.1  [/FONT]
it remains wrong even if i unplug the external screen.
this happens though i did not choose mirroring in the screen prefs.

do you have any clue?
thanks in advance

---

### Post by gaboro on 2009-12-26
Hiya,

Seems my laptop screen delivers a wrong eeid. Having pluged the external monitor I have to add the proper modeline manually (using xrandr) for the laptop screen. For anyone who have the same problem, the modeline can be found in the /var/log/Xorg.0.log.

---

