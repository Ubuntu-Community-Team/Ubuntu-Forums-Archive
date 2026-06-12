---
title: "xrandr - added new resolution but dual-screen messed up."
date: 2011-07-29
forum: General Help
---

### Post by Unhackmee on 2011-07-29
When i connected a second monitor to my laptop (800x600), the second monitor's resolution wasn't available initially. I did some google magic and ended up with the following code to get the monitor to its correct view:
```
xrandr --newmode "1280x1024_59.90"  108.70  1280 1360 1496 1712  1024 1025 1028 1060  -HSync +Vsync

xrandr --addmode VGA1 1280x1024_59.90

xrandr --output VGA1 --mode 1280x1024_59.90
```

Okay, so now the second monitor works fine and dandy on its own, but if i try to use both screens (ie: turn on laptop's screen aswell) the display gets messed up. When i turn the laptop screen on, both screens freeze and the wallpaper goes all black, and it remains frozen. All the panels, including the unity launcher are visible - but remain unresponsive.

I have fiddled around with some setups and I have discovered that the problem occurs only when I position the laptop screen on the right or left of the monitor. It isnt stuck when i position the laptop screen beneath or ontop of the monitor, but applications cant seem to identify screen borders- i mean they don't maximize properly! 

Anyways, i need to get this thing up and working ASAP. The laptop screen needs to be on the left of the monitor. so anything even slightly helpful would be appreciated.
[SIZE="1"]I could try to get a screenshot of the frozen screen, but no guarantees [/SIZE]

---

### Post by realzippy on 2011-07-29
what is the output from
```
xrandr -q
```
when both panels are powered one during boot ?

---

