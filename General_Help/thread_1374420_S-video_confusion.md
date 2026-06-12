---
title: "S-video confusion"
date: 2010-01-06
forum: General Help
---

### Post by Silent183 on 2010-01-06
So I'm running Ubuntu 9.10 and having trouble hooking my tv up to my HD2600 pro agp card. When I open CCC my tv is detected but for some reason I cannot for the life of me get my desktop to show up on my tv. As for video card drivers I'm using this: [http://support.amd.com/us/gpudownload/linux/Pages/radeon_linux.aspx?type=2.4.1&product=2.4.1.3.2&lang=English]("http://support.amd.com/us/gpudownload/linux/Pages/radeon_linux.aspx?type=2.4.1&product=2.4.1.3.2&lang=English")

When I open a terminal and use the: xrandr -q command this is what I get:

Screen 0: minimum 320 x 200, current 1280 x 1024, maximum 1280 x 1280
DFP1 disconnected (normal left inverted right x axis y axis)
DFP2 disconnected (normal left inverted right x axis y axis)
CRT1 connected 1280x1024+0+0 (normal left inverted right x axis y axis) 338mm x 270mm
   1280x1024      60.0*+   75.0  
   1280x720       60.0 +
   1280x960       60.0  
   1152x864       75.0     60.0  
   1280x768       59.9  
   1024x768       75.0     60.0  
   800x600        75.0     60.3  
   720x480        60.0  
   640x480        75.0     60.0  
   640x432        60.0  
   640x400        75.1     59.9  
   512x384        60.0     74.9  
   400x300        75.0     60.7  
   320x240        75.6     60.0  
   320x200        75.5     60.1  
CRT2 disconnected (normal left inverted right x axis y axis)
TV connected (normal left inverted right x axis y axis)
   1024x768       30.0 +
   800x600        30.0 +
   720x576        30.0 +
   720x480        30.0 +
   640x480        30.0 +
   640x432        30.0 +
   640x400        30.0 +
   512x384        30.0 +
   400x300        30.0 +
   320x240        30.0 +
   320x200        30.0 +
COMPONENT_VIDEO disconnected (normal left inverted right x axis y axis)


Can anyone help me out with this?

---

### Post by Silent183 on 2010-01-07
bump

Anybody know how I can get this working?

---

### Post by mdrake36 on 2010-01-07
Went throught the Same thing last night. Tried every resolution and Frame rate. It works fine on the Boot screens but as soon as the Desk top Gnome boots .... Bye Bye...... in walks Blankscreen but whats weird is even the VGA is gone the drivers must be missing something.

---

### Post by mdrake36 on 2010-01-08
[COLOR=#980101]**[ubuntu]**[/COLOR] [[COLOR=#000000]S-video boot problems[/COLOR]]("http://ubuntuforums.org/showthread.php?t=1357324&highlight=s-video") 
can2002 
 
This Old thread seems helpful haven't tried it but sounds like a start.

---

