---
title: "Default Screen"
date: 2009-11-06
forum: General Help
---

### Post by awuja on 2009-11-06
Hi everyone, hope you're all OK :)

I have searched Google and these Forums to no end to try and solve this..

I've installed 9.10 and it is all going great, however my resolution is fine.

I've entered xrandr in to the Terminal and get the following:

VGA1 connected 1360x768+0+0 (normal left inverted right x axis y axis) 0mm x 0mm
   1360x768       59.8* 
   1152x864       60.0  
   1024x768       60.0  
   800x600        60.3  
   640x480        59.9  
LVDS1 connected 1360x768+0+0 (normal left inverted right x axis y axis) 0mm x 0mm
   1680x1050      59.9 +   84.9     74.9     69.9     60.0  
   1600x1024      60.2  
   1400x1050      85.0     74.8     70.0     60.0  
   1280x1024      85.0     75.0     60.0  
   1440x900       59.9  
... etc

The problem is that I want LVDS1 to be my 'default' (I only have 1) monitor as the correct resolution is 1680x1050 which isn't shown in VGA1

The problem corrects itself if I type

xrandr --output LVDS1 --auto

but I don't want to have to do this every time I log in.. is there anyway that it can be done automatically or permanently?

p.s. I've tried adding a script to /etc/init.d making it executable etc but it didn't work :/

Thanks for reading!

awuja

---

### Post by awuja on 2009-11-06
Solved:

After typing xrandr --output LVDS1 --auto

Go to System>Preferences>Display and click on Detect Monitors which will apply it permanently.
[B]
::EDIT::[/B]

This only applys the resolution once I have logged in, not at the login screen.

Also, I now have an "unknown monitor" showing in my display settings... and a new Screen 0 listed in xrandr.

*sigh*

any suggestions?

---

