---
title: "Screen Brightness Twitching and Freaking out"
date: 2010-01-22
forum: General Help
---

### Post by JacKeown on 2010-01-22
My laptop with Ubuntu 9.10 just randomly while adjusting the brightness using the shortcut key commands on my laptop the brightness started to glitch between two brightness levels. If I don't use the shortcut keys it doesn't glitch unless I shut the screen or restart the computer.  So I've had to put up with this for the past couple months now and I think that it might even drive me to reinstall but then I lose all my data. :(  

Anybody please help.......
thanks in advance

---

### Post by shea279 on 2010-02-26
I'm having the same problem..
for example if i turn the brightness down with the function key on my keyboard, it jumps to first like 75% brightness, then 30%, then 80%, then 0%, then back to 75% and repeats. (or something like that)

Also, if I leave my computer alone for ~30 seconds while on battery, the screen brightness goes down a notch, and if i move the mouse it goes down another notch (which i manually have to correct).

---

### Post by PoHandle on 2010-02-26
Try messing with some of the settings in Power Management. ( System > Preferences > Power Management )

I don't have the same twitching issue, but I did experience problems with an extremely dim backlight until I changed some power management settings under the "On Battery Power" tab.

---

### Post by neoroses on 2010-02-26
give this ago, stop the computer messing with its own brightness levels

```
gconftool -s /apps/gnome-power-manager/ambient/enable -t bool false
```

---

