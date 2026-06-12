---
title: "Ignore mouse when locked?"
date: 2011-10-15
forum: General Help
---

### Post by darthpenguin on 2011-10-15
Hi Guys. When I set the Screen settings on Ubuntu 11.10 to turn off the screen after 10 minutes it doesn't actually turn off the screen it just blanks the screen (like a blank screensaver). Turning off the screen should have that same effect as running this command ```
xset -display :0 dpms force off
``` I suppose that is more like standby not power off. But the point is the screen's backlight turns off. That's not a big deal because I can bind the above command to an alias or keyboard shortcut or whatever. The big problem is the smallest movement of the mouse wakes the screen and it won't shut off again unless I manually power off the screen or log in and run the above command again. Is there a setting (like in gconf) that will make the screen ignore mouse movement but still wake from mouse buttons or keyboard?

---

