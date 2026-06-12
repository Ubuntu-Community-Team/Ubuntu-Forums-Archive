---
title: "monitor resolution; samsung syncmaster3 cvm4967p"
date: 2006-06-28
forum: General Help
---

### Post by Keith_Beef on 2006-06-28
I'm sure that I've run this monitor at a higher resolution in the past. At the moment, it's at 800 x 600 @ 70Hz.

I generated modelines using [http://www.dkfz-heidelberg.de/spec/linux/modeline/](http://www.dkfz-heidelberg.de/spec/linux/modeline/) for 1024 x 768 @ 86.8 Hz and @ 70 Hz:

```
# V-freq: 86.80 Hz  // h-freq: 70.33 KHz
Modeline "1024x768" 100.20  1024 1080 1200 1424   768  768  771  810
# V-freq: 70.00 Hz  // h-freq: 56.12 KHz
Modeline "1024x768" 74.10  1024 1064 1152 1320   768  768  770  801

```

The V-freq values look too high, compared to the specs I found.

Is there an ergonomic tool for setting up monitor resolution, without having to edit the X config file by hand?

Please, no jokes about emacs being more ergonomic than vi. I think I've heard them all before ;)

Beef.

---

### Post by marcolinuxbr on 2007-02-25
I managed my syncMaster3  to work with 1024x768 

This is a section from my /etc/X11/xorg.conf ( knoppix 5.1.1 xorg  7.1.1)

############################
Section "Monitor"
        Identifier      "SyncMaster3-FlickALot"
        Option  "DPMS"  "true"
        HorizSync    31.5-38 
        VertRefresh  70-86.8 

#this modline dont work right away. 
#Modeline "1024x768@75" 95.52 1024 1056 1376 1408 768 782 792 807
#got it from [http://xtiming.sourceforge.net/cgi-bin/xtiming.pl](http://xtiming.sourceforge.net/cgi-bin/xtiming.pl)
#I needed xvidtune (click auto and left some times to get the next modline below) 

# this works !!! but dont expect too much from this old monitor ok? 
#interlace,  flickalot 
Modeline "1024x768"     44.90   1024 1040 1216 1288    768  768  776  813 +hsync +vsync interlace

EndSection
############################



Put this in section screen:
############################
Section "Screen"

#............More stuff here

        Monitor    "SyncMaster3-FlickALot"

#............ More stuff here
EndSection
############################

Another useful link:
[http://en.wikipedia.org/wiki/XFree86_Modeline](http://en.wikipedia.org/wiki/XFree86_Modeline)

Hope this help. 
Certainly will help me in the future. as I always lose those configs :-)

---

