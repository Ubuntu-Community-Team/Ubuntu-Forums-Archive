---
title: "Dual screen: second screen isn't working anymore"
date: 2012-05-29
forum: General Help
---

### Post by dudeeh on 2012-05-29
I have a pc with an nvidia 8600gts which has one HDMI connector and one DVI connector. I have had a dual screen setup working perfectly since at least 9.04 but due to a harddrive crash I did a fresh install (as opposed to my regular "upgrade" routine) of 12.04.

My main screen (dvi) is setup to use 1920x1200 while my second screen is set up to use 1920x1080. The second screen behaves "odd" to say the least. When I first turned it on, it went black half the time, then finally it "stabilized" into a fuzzy desktop. By fuzzy I mean the text looks mangled etc, it looks as if the resolution is wrong. On top of that the second screen popped up a warning that it was not running in its optimal resolution (being 1920x1080). And yet xrandr had this output:

Screen 0: minimum 320 x 200, current 3840 x 1200, maximum 8192 x 8192
DVI-I-1 connected 1920x1200+0+0 (normal left inverted right x axis y axis) 518mm x 324mm
   1920x1200      60.0*+
   1920x1080      50.0     60.0  
   1600x1200      60.0  
   1680x1050      60.0  
   1280x1024      60.0  
   1440x900       59.9  
   1280x960       60.0  
   1280x800       59.8  
   1280x720       50.0     60.0  
   1024x768       60.0  
   800x600        60.3     56.2  
   720x576        50.0  
   720x480        59.9  
   640x480        60.0  
HDMI-1 connected 1920x1080+1920+0 (normal left inverted right x axis y axis) 531mm x 298mm
   1920x1080      59.9*+
   1680x1050      60.0  
   1280x1024      75.0     60.0  
   1440x900       59.9  
   1280x960       60.0  
   1280x800       59.8  
   1152x864       75.0  
   1280x720       60.0  
   1024x768       75.1     70.1     60.0  
   832x624        74.6  
   800x600        72.2     75.0     60.3     56.2  
   720x480        59.9  
   640x480        72.8     75.0     66.7     60.0  
   720x400        70.1  

When I take a screenshot, the second screen looks OK so I can't actually show you how it appears to me. I thought the screen itself might be malfunctioning but if I enable that screen alone, it works like a charm. Even tried it on another pc (as standalone screen) and it worked perfectly.

On a sidenote: I tried the official nvidia binary drivers as well, there the second screen simply would not budge. It stayed black no matter what setting I tried. Fun fact though: if I take a screenshot with the official nvidia drivers enabled (and the second screen black), it still shows a proper dual screen setup.

If I recall correctly, on the previous setup (before the crash), I was using the proprietary driver but I'm not entirely sure.

On a further note: in light of this topic, I tried to start up the "displays" tool again at which point the desktop became unresponsive. I had to restart the lightdm service to get it back up.

Any ideas what could be causing this?

---

