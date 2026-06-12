---
title: "Screen resolution problem"
date: 2011-02-07
forum: General Help
---

### Post by Kaimbelic on 2011-02-07
Hello guys,
i am fairly new to ubuntu and Linux as a matter of fact.
i have been trying for hours to read forums/troubleshot
but not one has worked.


So here is my problem:

I am running Ubuntu 10.10 with a Nvidia Geforce 1600 gs (old ... i know)
hooked up to a Panasonic Viera 32"

I have all the lates drivers form nvida and what not

The problem i that the screen (desktop), no matter what the resolution is, always is bigger then the screen itself. I am pretty for sure i might just be a panning issue but i have no idea how to fix that and i have tried alot of tuts on it.

I have tried the :
[https://wiki.ubuntu.com/X/Config/Resolution](https://wiki.ubuntu.com/X/Config/Resolution)
setp on config

but on the first part 
"
 xrandrshows you the names of different outputs available on your system (LVDS, VGA-0, etc.) and resolutions available on each: 

Screen 0: minimum 320 x 200, current 1400 x 1050, maximum 1400 x 1400
VGA disconnected (normal left inverted right x axis y axis)
LVDS connected 1400x1050+0+0 (normal left inverted right x axis y axis) 286mm x 214mm
   1400x1050      60.0*+   50.0  "

Mine shows xrandr: failed to get the gamma for output default           //( and how do i change output names and what not)

screen 0: minimum 320x240, current 1280 x 720, maximum 1280 x 720
default connected 1280x720+0+0 0nn x 0mm
1280x720   50.0* 51.0
800x600    52.0
720x400    53.0  54.0
640x480    55.0  56.0
400x300    57.0
320x240    58.0

by the way the max resolution for the tv its self is 
1366x768
the connection i am useing btw is a DVI to HMDI converter straight into the tv.

hope someone can help me xD!

---

### Post by dcstar on 2011-02-08
> **Kaimbelic said:**
> 
..........
The problem i that the screen (desktop), no matter what the resolution is, always is bigger then the screen itself. I am pretty for sure i might just be a panning issue but i have no idea how to fix that and i have tried alot of tuts on it.

I have tried the :
[https://wiki.ubuntu.com/X/Config/Resolution](https://wiki.ubuntu.com/X/Config/Resolution)
.........
by the way the max resolution for the tv its self is 
**1366x768**
the connection i am useing btw is a DVI to HMDI converter straight into the tv.

hope someone can help me xD!

You will probably have to manually set the maximum resolution in the xorg.conf file because the HDMI/DVI converter may not be connecting all the necessary pins for auto-detection:

[https://wiki.ubuntu.com/X/Config/Resolution#Setting%20resolution%20changes%20in%20xorg.conf](https://wiki.ubuntu.com/X/Config/Resolution#Setting%20resolution%20changes%20in%20xorg.conf)

---

### Post by Kaimbelic on 2011-02-08
> **dcstar said:**
> You will probably have to manually set the maximum resolution in the xorg.conf file because the HDMI/DVI converter may not be connecting all the necessary pins for auto-detection:

[https://wiki.ubuntu.com/X/Config/Resolution#Setting%20resolution%20changes%20in%20xorg.conf](https://wiki.ubuntu.com/X/Config/Resolution#Setting%20resolution%20changes%20in%20xorg.conf)


thanks for the help xD
going to try it but right now i am using an DVI to VGA an using the vaga port and it works like a charm

but i am going to try the config my self to make sure xD!

---

