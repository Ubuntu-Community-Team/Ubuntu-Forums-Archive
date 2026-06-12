---
title: "Blank Desktop"
date: 2010-07-09
forum: General Help
---

### Post by goldenatom on 2010-07-09
I just installed Lucid Lynx on my mom's old desktop. It's a 1.2ghz p3, 1gb of ram, and intel's integrated graphics from that era. It has run previous versions of ubuntu through 9.x just fine. 

I decided to do a clean install of Lynx. Everything went fine, but after I log in, the desktop is completely blank. All I see is the default wallpaper. No icons, no task bar. I can right click and get that menu, but that's all. 

What's up?

---

### Post by cjtemple on 2010-07-09
[COLOR=black][FONT=Verdana]Just kinda spit balling here, but is it possible that your screen resolution is set just high enough for the edges to extend beyond the screen?[/FONT][/COLOR]

---

### Post by lidex on 2010-07-09
Try booting into recovery mode. Drop into the root shell with networking and run this command:
```
apt-get install ubuntu-desktop
```
Restart.

---

