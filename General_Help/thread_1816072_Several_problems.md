---
title: "Several problems"
date: 2011-08-01
forum: General Help
---

### Post by Mirkovich on 2011-08-01
Currently I have 10.04 LTS 64-bit.

a- Randomly (it seems to happend half of the time I update the kernel), the keypad of my notebook (Acer Aspire 5552-3343) stops working as a numerical keypad. Instead, pressing num lock switches between home/end/pgup/pgdn functions and to move the mouse (**How do I make it to work again with the numbers?**).
b- Some day (on an update or maybe with an incorrect power off, I dont know when) my computer stopped loading snd-hda-intel. I have to **modprobe** it **manually** everytime I power up the notebook, or I don't have any sound at all. Approximately the same time, HP manager stopped seeing my wireless printer (it asks me to connect it thru USB). (**Is there a file that should load my sound driver? What's that file? Is it corrupt?**)
c- Everytime I power it on, brightness is at a maximum, and in my previous notebook, I recall it saved brightness value when I power it off. (**Software? Hardware? How can I make Ubuntu remember that?**)
d- I do put my notebook A LOT to sleep. Everytime I do that, it tries to reconnect to the same wireless network, even when I'm not there anymore (it's a notebook, so I put it to sleep everytime I move, and everytime I wake it up, it still seeing the last wireless for like 5-10 minutes... and as it cant reconnect just because that wifi is out of reach, it asks me for the password instead of connecting to the other preferred wifi). I mean, if I travel while my notebook is sleep, **Ubuntu never notices** that wifi is out of reach. It just keeps trying to reconnect.
e- There's some memory leak and I cant find it. After using several programs for several days, like opening and closing Virtualbox, OpenOffice, Firefox, Thunderbird, etc. If I close all of them, the machine still slow and memory used still high. No other option but to reset (**JUST LIKE WINDOWS :/**). As of now, adding all the memory from all the programs (from process tab), according to System Monitor, it gives me neat 1Gb of ram, but in resources tab it says I'm using 1,5 Gb (I dont think kernel's buffer should be 500 Mb). This last number usually grows up after some days of working (given that I put the notebook to sleep), and the machine finally becomes slow when it uses swap. So then I have to reset and system's fresh and fast again.
f- After every reset, the session miniaplication is resized incorrectly.
g- Don't know if this is a Flash, Ubuntu or Firefox problem, but Flash is working badly on my notebook. Same Firefox on Windows works just fine. But in my notebook, sometimes flash works badly, and other times, opening a new tab that uses flash makes **the other tab** having youtube to hang up (sometimes with some images from the other tab). Tried reinstalling both Flash and Firefox and problem still. Upgraded to Firefox 5 and the problem still.

Any help?

Thanks in advance.

---

### Post by owise1 on 2011-09-30
Hi Mate - had the num lock problem as well and thought it was a crook keyboard so swapped over and no change.  A quick search of this forum showed that a Ctrl shift Num lock will fix it.  I do VNC into this machine and that uses some funny key sequences and I may have hit the above combination by mistake.  See how you go.

Dave

---

