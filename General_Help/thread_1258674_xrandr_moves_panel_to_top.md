---
title: "xrandr moves panel to top"
date: 2009-09-05
forum: General Help
---

### Post by hanlin on 2009-09-05
I have a laptop connected to an external monitor. I'm trying to use xrandr to change between display settings. My code is as follows to move the display from the external to the laptop:

#!/bin/bash

xrandr --output VGA1 --off
xrandr --output LVDS1 --auto

While this works nicely in changing displays, the bottom panel moves up to the top for some reason. It does that too when moving from laptop only to external. 

I was wondering if there was a way to move the panel back down to the bottom by adding another line of code. I am running Karmic, btw. I don't know if this is a bug in karmic as I've never tested this with previous versions.

---

