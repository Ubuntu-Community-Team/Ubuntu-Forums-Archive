---
title: "Wrong video aspect ratio"
date: 2011-05-16
forum: General Help
---

### Post by Aquila99 on 2011-05-16
I have just installed 11.04 on an eeePC B602 connected to my LG TV over HDMI

All runs fine, except the video is at the wrong aspect ratio. (this results in everything looking too fat!

Running the Preferences->Monitor utility shows that I have 1024x768 resolution selected at 75Hz (good!, as that is what the TV manual recommends), but it says that the aspect ratio is 4:3, but I want 16:8

running xrandr gives

Screen 0: minimum 320 x 200, current 1024 x 768, maximum 8192 x 8192
HDMI-0 connected 1024x768+0+0 (normal left inverted right x axis y axis) 828mm x 620mm
   1024x768       60.0 +   75.1*    70.1  
   1280x720       50.0  
   800x600        72.2     75.0     60.3     56.2  
   720x576        50.0  
   640x480        72.8     75.0     60.0     60.0  
   640x360        70.1  

Interesting, the physical dimensions reported 828mm x 620mm which is 4:3, but I want 694x393mm (I measured it with a ruler), which is 16:9

If it helps, the card is a Radeon HD3400 series

So, what do I do next, in the good-old-days, you could just edit xorg.conf, but it seems that this no longer exists.
I am guessing that there is an xrandr command to change it, but after reading the man page for a while and playing around, could not get it to work.

Please help

---

### Post by aeiah on 2011-05-16
you have two choices:
use a 16:9 AR resolution, such as HD 720p (1280x720) or stick with 1024x768 and alter the aspect ratio of video files only, using your video playing software (mplayer, vlc, xbmc etc)

using 1280x720 is the best solution, but its likely that you'll have your screen edges missing (due to overscanning). you can fix this with options on the tv sometimes, but you might have to find a software solution if that isnt possible.

---

### Post by Grenage on 2011-05-16
Rectangular pixels, hooray. ;)

[This]("http://www.mythtv.org/wiki/Display_Size") may be of some use to you.

---

### Post by Aquila99 on 2011-05-16
Thanks for the advice aeiah.
I tried using the HD 720p (1280x720) resolution, but the top of the screen was chopped off (lost the menu bar at the top, which makes selecting menus tricky!)
I could not find a TV option to fix this (and anyway, I switch between HDMI inputs)

And thanks too Grenage
I had a look.  I thought that the xorg.conf file was deprecated?  That is why I was fiddling around with xrandr
I was just trying the --scale option in xrandr, and although it looked promising, nothing changed!

---

### Post by Grenage on 2011-05-16
> **Aquila99 said:**
> I thought that the xorg.conf file was deprecated?  That is why I was fiddling around with xrandr
I was just trying the --scale option in xrandr, and although it looked promising, nothing changed!

It is, but it will still function if the file exists; for example, you can specify *some* of your settings, and the system will fill in the blanks, so to speak.

xrandr is generally recommended as it's far more dynamic, but if you have no luck there, try xorg.conf.  The basic information detailed in that guide should be all you need to enter; just make sure the settings are appropriate for your TV.

---

### Post by Aquila99 on 2011-05-17
Solved the issue.
After many hours playing with xrandr, decided to go on another tack.
Installed the proprietary ATI Catalyst driver (from Administration->Hardware Drivers)
Now I get lots of modes to select from, including the proper native resolution at 16:9 and with an easy slider to control the over-scan so that it fits exactly in the screen (and lots of other settings to play with)

Now it plays video etc perfectly.

Its a shame, I would have preferred the open source driver ...

---

### Post by Grenage on 2011-05-17
A win is a win, at least it's working now!  Does the ATI driver create an xorg.cony, as the nvidia drivers do? If so, you may be able to take its config and use that with the open drivers.

---

### Post by Aquila99 on 2011-05-19
Yes, it did create an xorg.conf file with a minimalist settings to load the ATI driver.
I am not quite sure where it stores all the driver settings from the control panel.
Anyway, it seems to work fine, even got it up to 1920x1080, the maximum supported by the TV (even though at only 30Hz)

Although, perhaps not!, just had a kennel slowdown after a reboot (even ssh into the box was slow).  But I suspect it was the USB IR control adapter ... need to debug more on the weekend.   Too many late nights already on this issue. And I changed too many things at once.

---

