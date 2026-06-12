---
title: "nopowerconnectorcheck"
date: 2011-04-02
forum: General Help
---

### Post by vincentpersichetti on 2011-04-02
Hey guys. Long time reader first time poster. 

I have this problem that I've spent days looking for an answer so this is my last resort, I promise.

I installed ubuntu 10.10 on a desktop to use for a media server, and plus some. Everything worked! I proceeded to install the nVidia driver for the 9800gt After it was installed I rebooted per the notification after installation. 

So now my computer loads directly into terminal and I can't start the GUI. I tried startx but it gave that whole warning about the "nopowerconnectorcheck" blah blah blah. 

So I've done my research and I bought a 650w psu. Still no dice. 

I know that there is a way to turn off the power connector check but I have no Idea how. 

Please help. Thanks,

Chris

PS The driver number is 260.19.44

---

### Post by Quackers on 2011-04-02
Welcome to UF
After some searching about (as I was sure I had seen this error before) it seems that some graphics cards when used with certain hardware configurations need the "nopowerconnectorcheck" option to be entered at the end of the "screen" section in the /etc/X11/Xorg.conf file as shown in post #4 of this old post (but I suspect the same thing holds true now - maybe!
[http://www.linuxforums.org/forum/debian-linux/39041-needing-graphics-help.html](http://www.linuxforums.org/forum/debian-linux/39041-needing-graphics-help.html)

---

### Post by Quackers on 2011-04-02
Here's a more recent one with similar info
[http://kubuntuforums.net/forums/index.php?topic=3112609.0;imode](http://kubuntuforums.net/forums/index.php?topic=3112609.0;imode)

---

