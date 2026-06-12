---
title: "Jaunty login has extremely small fonts"
date: 2009-09-20
forum: General Help
---

### Post by freezerburnt on 2009-09-20
I'm pretty sure that this has been posted many times already, but I can't seem to find a posted solution to fixing the EXTREMELY small fonts I get on the login screen for Ubuntu. I've tried looking for a fix in the gdm.conf file ( [http://ubuntuforums.org/showthread.php?t=1230972&highlight=small+login+fonts](http://ubuntuforums.org/showthread.php?t=1230972&highlight=small+login+fonts) ), but nothing seems to work.....
Pls.... does anyone have a solution for this problem???

Freezerburnt

---

### Post by CatKiller on 2009-09-21
When I saw this, it was because X's calculated [DPI]("http://en.wikipedia.org/wiki/Dots_per_inch") value was wrong. I corrected it by putting the monitor size in the Monitor section of my xorg.conf (using the DisplaySize parameter), although the correction you use may be different if the cause of the incorrect DPI value is different. /var/log/Xorg.0.log may tell you more.

---

