---
title: "Killed my display - how do I reset the settings?"
date: 2011-10-12
forum: General Help
---

### Post by conal on 2011-10-12
Hi, I just changed the refresh rate in the display settings on xubuntu 10.10. The screen went blank. When I restart I get the log in screen and I can use the recovery console - I have tried a few instructions with xrandr to set it to different refresh rates but none of them work - always goes blank when I log in, I have also tried to delete the configuration file with:

```
sudo rm ~/.config/monitors.xml

```
or 

```
sudo rm /home/conal/monitors.xml
```

but both of these say "no such file or directory"

BASICALLY: Is there a way to completely reset the display settings in xubuntu 10.10?

The display worked out of the box on install - this problem was cause by me idly clicking about - doh! 

I usually post in the apple forums as this is a powerPC eMac, but I don't think this question is specific to the powerPc architecture - or to macs.

Any help would be much appreciated!!!

Thanks in advance 

Conal

---

### Post by collisionystm on 2011-10-12
> **conal said:**
> Hi, I just changed the refresh rate in the display settings on xubuntu 10.10. The screen went blank. When I restart I get the log in screen and I can use the recovery console - I have tried a few instructions with xrandr to set it to different refresh rates but none of them work - always goes blank when I log in, I have also tried to delete the configuration file with:

```
sudo rm ~/.config/monitors.xml

```or 

```
sudo rm /home/conal/monitors.xml
```but both of these say "no such file or directory"

BASICALLY: Is there a way to completely reset the display settings in xubuntu 10.10?

The display worked out of the box on install - this problem was cause by me idly clicking about - doh! 

I usually post in the apple forums as this is a powerPC eMac, but I don't think this question is specific to the powerPc architecture - or to macs.

Any help would be much appreciated!!!

Thanks in advance 

Conal

use  Xrandr

see this... 

[http://pihalf.wordpress.com/2009/11/16/set-your-monitor-refresh-rate-with-xrandr/](http://pihalf.wordpress.com/2009/11/16/set-your-monitor-refresh-rate-with-xrandr/)

Google for others

xrandr change refresh rate

---

### Post by conal on 2011-10-12
Ooooh, that might work! I'll get back to you shortly (no laptop or printer so gonna have to write this down and go to broken box!).

---

### Post by conal on 2011-10-12
Well that definitely restarted the display while I was using recovery mode, but still when log in the screen goes blank - I think this must be something user specific?!

---

