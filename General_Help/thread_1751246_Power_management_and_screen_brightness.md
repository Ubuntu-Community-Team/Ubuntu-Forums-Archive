---
title: "Power management and screen brightness"
date: 2011-05-06
forum: General Help
---

### Post by pkosmas on 2011-05-06
Hi all,

New to ubuntu, i recently installed 11.04 x64 on a samsung R580 (core i3,Nvidia GT330M) laptop.
Been very satisfied so far, things working smoothly for me.
Just one thing i cant seem to get right... Is there any way to make the system remember my brightness settings according to whether its plugged in or not? 

I mean, i want full screen brightness when plugged in, and say 50% when i unplug... Anyway to set system to do it automatically??

Also, any way to set system so that it automatically hibernates after set time of inactivity???

Appreciate your help...

---

### Post by pkosmas on 2011-05-06
I've come closer to a solution... opening gconf-editor, under apps-gnome power manager-backlight,i see a string brightness_dim_battery with a value set 50... I tried to change this to 60 but i get an error: see image

Any ideas how to overide???

---

