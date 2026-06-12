---
title: "Gnome screenshot - window bigger than screen"
date: 2012-09-09
forum: General Help
---

### Post by EgoGratis on 2012-09-09
if i use command:

gnome-screenshot -w

It works fine but i would need bigger window that does not fit inside available area of my screen and it does not work. Is there a way i could grab content of the window that is bigger then screen area too.

---

### Post by EgoGratis on 2012-09-09
I think i actually found solution after struggling with this the whole day and i will post it here if in the future somebody finds this info useful and here it is:

Example:
-Max (resolution) screen size: 1280x1024
-Window size: 1920x1080

Use command xrandr -q to determine maximum screen size and then try to increase framebuffer size inside those boundaries:

xrandr --fb 2500x1500

If windows of size 1920x1080 will fit in screenshot will be made just like it should be in the first place (1920x1080). 

To set default settings:

xrandr --fb 1280x1024

---

