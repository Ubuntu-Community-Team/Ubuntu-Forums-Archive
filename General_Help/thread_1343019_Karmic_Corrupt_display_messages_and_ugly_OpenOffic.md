---
title: "Karmic: Corrupt display messages and ugly OpenOffice/Acrobat"
date: 2009-12-01
forum: General Help
---

### Post by aextance on 2009-12-01
The notification messages appearing in my Karmic are corrupted, which hasn't really been a problem, although when I was working on the very last drops of juice in my laptop battery last week it would have been good to know what the system was telling me. 

Here's an example:

[ATTACH]138247[/ATTACH]

I also get some ugly looking dialogs in OpenOffice, which I suspect are another symptom of the same problem. Here's another shot:

[ATTACH]138248[/ATTACH]

Generally so far Karmic has been much better than Jaunty for me, but in installation I got stuck at a black screen and had to complete the process at the command line with an internet connection. I wonder whether this is part of my problem.

Any ideas what the problem is, and how I fix it?

---

### Post by mack75 on 2009-12-01
Hi aextance:

Has you tryied with the compiz disable?

Second, you did a fresh installation? if not, can you moving your configurations directories and try it again?

cd ~
mkdir oldconfig
mv .compiz oldconfig
mv .config oldconfig
mv .gconfd oldconfig
mv .gconf  oldconfig
mv .gnome2 oldconfig
mv .gnome2_private oldconfig

Or you can try with a new theme, this seem like a library render issue.

Regards!

---

### Post by audiomick on 2009-12-01
At a guess, the desktop theme is messed up somehow, but that is really only a guess.

---

### Post by aextance on 2009-12-01
I don't run Compiz, as in Jaunty the Intel driver issue took up way too much of the RAM on my slightly outdated machine. 

The issue with OpenOffice can be fixed by changing the appearance to a different theme, but not the messaging problem. 

Can I just check with your instructions, mack75, are you saying that your instructions are all I would have to do to remake my configuration directories? Or would I have to do something else as well, like, say, restart my computer?

---

### Post by mack75 on 2009-12-01
Yes these are all that you need to remake your config. And all thats remains is logout and login again.

---

### Post by aextance on 2009-12-01
OK, well, that didn't work. Same corrupt notifications, same problems with OpenOffice and Acrobat Reader. Got slightly freaked when I tried to start Evolution and found that my emails weren't there, but managed to put everything back OK now. 

Changing appearance sorts the problem in OpenOffice, but not notifications, and not all other appearances do this. "Dust" and "Human" and their relations are out, I'm currently using "Crux", which is an improvement. 

I don't want to do a clean install for what is essentially just an annoyance... but I would be pleased to be rid of the annoyance.

---

### Post by aextance on 2009-12-07
OK, so I actually did do a clean install in a moment of curiosity/weakness/stupidity. It only took about a day and a half. And guess what? The display problem is still there.

One interesting thing that I have observed from Karmic being set to have "normal" visual effects as default is that my messages appear as they should do under the "normal" setting. However, the whole rest of the display is corrupt then. When I turn visual effects to "off" the majority of the display clears up, but the messages are corrupt. I'll try and upload some pics when I've got my main machine sorted out properly, but in the meantime does anyone have any thoughts?

---

### Post by autocrosser on 2009-12-09
I helped Emerald-girl get her T30 OSD running---sorry to say that the Thinkpad OSD we were talking about is for the "special" keys on Thinkpads---not the "normal" OSD you are having problems with.....

I'm interested in your problem--what kind of hardware are you using? Any Closed-source drivers---ATI or Nvidia? Laptop or desktop? It would really help to know.  There were  problems with the ATI drivers during Karmic development.........

---

### Post by aextance on 2009-12-28
I did end up reinstalling Ubuntu shortly after I started this thread, and have basically just built it up to the profile I had from there since. I haven't installed any proprietary drivers though, it's been doing this straight out of the box, both after the upgrade from Jaunty and on a clean install. 

However I do have an ATI graphics card, in fact it's an ATI Technologies Inc Radeon Mobility M7 LW [Radeon Mobility 7500].

Should I have a scout around for how to solve ATI driver problems in Karmic?

---

### Post by aextance on 2010-01-03
OK, the main suggestions I've seen so far for this involve messing around with Xorg.conf. Given that this file is supposed to be obsolete in Karmic, is this really the best way to go?

---

### Post by autocrosser on 2010-01-03
I'm away from my T42 right now, but I'll post the xorg.conf I'm using in Karmic in about 5~6 hours....got to do some Mac OSX work outcall....

---

### Post by aextance on 2010-01-03
Don't worry - I've sorted it. 

My xorg.conf now looks like this:

Section "Device"
Identifier "ATI 7500"
Driver "ati"
BusID "PCI:1:0:0"
Option "AccelMethod" "XAA"
Option "RenderAccel" "off"
EndSection

It's the "RenderAccel" "off" option that's key. Accordingly changing the acceleration method from XAA to EXA does something similar at the cost of lower performance.

The same bug is detailed at the following links:

[https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-ati/+bug/416001](https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-ati/+bug/416001)

[https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-ati/+bug/426582](https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-ati/+bug/426582)

[https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-ati/+bug/429295](https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-ati/+bug/429295)

Thanks for your help!

---

