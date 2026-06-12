---
title: "Overscan problem - how to fix?"
date: 2010-03-24
forum: General Help
---

### Post by Timewall on 2010-03-24
I'm running Xubuntu 9.10 through my Phillips HDTV - the screen overscans to the right, leaving about a third of an inch gap on the left.  I'm a newbie, so bear with me if this is a silly thing to ask about.  My xorg.conf is blank and my resolution seems ok (it's set at 1280X720, although my TV's resolution is 1280x768 ).

What are the steps necessary to fix this?  Thanks in advance for your help.

---

### Post by andrewc6l on 2010-03-24
You'll need to figure out the modeline for your xorg.conf file. The first place to try is running the program xvidtune - that will let you adjust things.

[http://ubuntuforums.org/showthread.php?p=454217](http://ubuntuforums.org/showthread.php?p=454217) (look for "how to adjust the position of your screen")
[http://www.trcompu.com/Computers/StartOver/XvidtuneHow-To.html](http://www.trcompu.com/Computers/StartOver/XvidtuneHow-To.html)

Sometimes xvidtune doesn't work (not sure why) - at that point, you can do it by hand. Here's a site that has some info:

[http://andrewmemory.wordpress.com/2009/10/30/tuning-x-video-with-modeline/](http://andrewmemory.wordpress.com/2009/10/30/tuning-x-video-with-modeline/)

---

### Post by Timewall on 2010-03-24
Ran xvidtune, got this:


"1280x720"     74.48   1280 1348 1484 1696    720  721  724  746 -hsync +vsync


I'm looking to put that in xorg.conf, but my xorg.conf is blank - how do I get it filled out with the necessary information, so I can use this generated modeline?

---

### Post by andrewc6l on 2010-03-26
You can get by with a fairly simple xorg.conf. Mine is:

```

Section "Device"
        Identifier      "Configured Video Device"
EndSection

Section "Monitor"
        Identifier      "Configured Monitor"
        Modeline "1280x1024_60.00"  109.00  1280 1322 1450 1700  1024 1027 1034 1066 -hsync +vsync
EndSection

Section "Screen"
        Identifier      "Default Screen"
        Monitor         "Configured Monitor"
        Device          "Configured Video Device"
EndSection


```

---

