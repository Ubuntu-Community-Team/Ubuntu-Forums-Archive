---
title: "I messed up the display settings"
date: 2009-08-04
forum: General Help
---

### Post by Ed187 on 2009-08-04
I made a stupid mistake.  I went to System > Preferences > Display and messed with the resolution.  It was at 16:9, but then I changed it to something smaller (I can't remember what exactly).  Now it is zoomed in and I can't change it back because the window doesn't go down far enough.
This is what I mean


[IMG]http://i276.photobucket.com/albums/kk40/Ed187/help.png?t=1249409138[/IMG]
Please, help a noob out.

---

### Post by credobyte on 2009-08-04
Open terminal and execute this command:
```
xrandr
```Once you see the list of available resolutions, execute:
```
sudo xrandr -s 1280x1024
```[COLOR=DimGray]** replace 1280x1024 with what you need[/COLOR]

---

### Post by Don1500 on 2009-08-04
> **Ed187 said:**
> I made a stupid mistake.  I went to System > Preferences > Display and messed with the resolution.  It was at 16:9, but then I changed it to something smaller (I can't remember what exactly).  Now it is zoomed in and I can't change it back because the window doesn't go down far enough.
This is what I mean


[IMG]http://i276.photobucket.com/albums/kk40/Ed187/help.png?t=1249409138[/IMG]
Please, help a noob out.

hold "ALT" and grab ("MOUSE 1") the window (anywhere) and move it up. (Or what he said)

---

### Post by Ed187 on 2009-08-04
> **credobyte said:**
> Open terminal and execute this command:
```
xrandr
```Once you see the list of available resolutions, execute:
```
sudo xrandr -s 1280x1024
```[COLOR=DimGray]** replace 1280x1024 with what you need[/COLOR]
Thanks!

---

