---
title: "Gnome Classic dual monitor config"
date: 2012-09-16
forum: General Help
---

### Post by Rob Sayer on 2012-09-16
Installed gnome shell yesterday on my laptop running12.04.  Using classic gnome ... SMplayer works perfectly now!  No more video stuttering.  I thought it didn't like the new mplayer builds (that was the problem under windows).  Apparently it's Unity it doesn't work well with.

Only thing is ... when I run it in dual monitor mode, it puts all the menu bars on the large external screen.  I want them on the laptop screen, and I haven't yet found anything in the docs to tell how to change this.

Can anybody point me in the right direction?

---

### Post by squaregoldfish on 2012-09-17
You can use xrandr for this. If you type xrandr on the command line, you get a list of screens:

```
Screen 0: minimum 320 x 200, current 3286 x 1080, maximum 8192 x 8192
LVDS1 connected 1366x768+0+0 (normal left inverted right x axis y axis) 344mm x 194mm
   1366x768       60.0*+
   1360x768       59.8     60.0  
   1024x768       60.0  
   800x600        60.3     56.2  
   640x480        59.9  
VGA1 connected 1920x1080+1366+0 (normal left inverted right x axis y axis) 477mm x 268mm
   1920x1080      60.0*+
   1680x1050      60.0  
   1600x900       60.0  
   1280x1024      75.0     60.0  
   1280x960       60.0  
   1152x864       75.0  
   1280x720       60.0  
   1152x720       60.0  
   1024x768       75.1     60.0  
   832x624        74.6  
   800x600        75.0     60.3  
   640x480        75.0     60.0  
   720x400        70.1  

```
The screen names in this case are LVDS1 (the laptop) and VGA1 (the external monitor). To change the primary screen (i.e. where the menus go, enter the following:

```
xrandr --output <screen name> --primary
```

Unfortunately X doesn't remember this setting for me. I don't need it often so it's not a problem, but you could put it in your Xinitrc or somewhere similar.

Steve.

---

### Post by Rob Sayer on 2012-09-17
Thanks for the reply ... got it working anyway.

---

