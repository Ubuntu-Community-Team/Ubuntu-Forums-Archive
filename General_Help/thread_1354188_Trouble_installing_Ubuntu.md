---
title: "Trouble installing Ubuntu"
date: 2009-12-13
forum: General Help
---

### Post by JerecDrak2 on 2009-12-13
Hey Guys,

I'm trying to install Karmic on a friend's computer, unfortunately I'm running into a problem I'm not too sure how to fix. When I boot the LiveCD up I get the glowing white throbber when USplash loads up, but when Xsplash comes into play the picture starts "looping" up and down the screen as the horizontal size of the picture slowly diminishes and then the screen goes blank. If I wait a while longer I can access the virtual terminals fine, but when switching back to the seventh one the same thing happens (except that instead of the Ubuntu logo that Xsplash displays it's the desktop that loops/shrinks/disappears).

His monitor is an ancient beige monstrosity (probably from mid/early 90s) so I reckon the X Server is trying to display at a resolution that the monitor doesn't support. Previously I would have tried to edit the xorg.conf file, however as it no longer exists I'm at a loss, does anyone know how I could fix this?

---

### Post by audiomick on 2009-12-13
As far as I know, if there is no xconf.org, the x server runs on defaults, but if there is one in the right place, it uses it.
Try putting one in where it belongs.
Mine, on 9.10, is at /etc/X11 and is definitely being used. I have a dual monitor setup with 2 different resolutions, which I very much doubt would work on the defaults. My video card is nVidia.

Otherwise, tell your mate to buy an up to date monitor. If his is that old, even a cheap modern one will be an improvement. ;)

---

### Post by miniyak on 2009-12-13
finding a free crt monitor on craig's list should be easy enough.

i use to have one of those old 600*800's i never could get it to work for some reason, though i'm sure with some know how its possible.

---

### Post by john newbuntu on 2009-12-14
You could try playing with the xrandr command and see if that helps you.
xrandr --output LVDS --off

---

### Post by audiomick on 2009-12-14
Instructions for that here:
[https://wiki.ubuntu.com/X/Config/Resolution](https://wiki.ubuntu.com/X/Config/Resolution)

---

### Post by JerecDrak2 on 2009-12-14
> **audiomick said:**
> Instructions for that here:
[https://wiki.ubuntu.com/X/Config/Resolution](https://wiki.ubuntu.com/X/Config/Resolution)

Thanks! Tried using the xrandr commands, unfortunately xrandr doesn't detect any displays :( 

I've done some googling and came across [this]("http://www.thinkwiki.org/wiki/Xorg_RandR_1.2"). I was wondering if stopping the X Server and then doing a sudo X -configure will work with Karmic? Especially if no displays are detected...

---

### Post by JerecDrak2 on 2009-12-19
So I finally got round to trying the sudo X -configure command and used the generated xorg.conf file, but this still didn't result in success. After looking over the file, I changed the display driver to vesa and the monitor worked! So it would seem that this is an issue with the radeon driver, which is a shame as now he's stuck with a terrible resolution and no 3D capabilities!

---

