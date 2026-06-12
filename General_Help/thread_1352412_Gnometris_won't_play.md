---
title: "Gnometris won't play"
date: 2009-12-11
forum: General Help
---

### Post by Skeezics on 2009-12-11
I installed Ubuntu 9.10 on 2 computers, both P4's with Windows XP running on both. On my primary machine (a very new P4) everything works 100 %. On the other P4 (an older one) I cannot get the game Gnometris to start. It opens the small box on the bar at the bottom of the screen and the little wheel spins for about 10 seconds and then just disappears and the box closes. All other games seem to be okay. I have removed the game and re-installed it. Still no change. I then un-installed Ubuntu and re-installed it again. Still the same.
 
I like that game very much and would like to have it working on that machine since I plan on taking it to my cottage for use on those dreary evenings.
 
Please help.

---

### Post by earthpigg on 2009-12-11
what does the terminal give you when you run the program from there?

the command is probably 'gnometris'

---

### Post by Skeezics on 2009-12-12
I get the following:
 
(gnometris:1471):ClutterGLX-CRITICAL **:Unable to find suitable GL visual. Failed to initialize clutter: Unable to realize the default stage
 
If I double click the icon in usr/games nothing happens at all.
 
Hope you can help.

---

### Post by earthpigg on 2009-12-12
> **Skeezics said:**
> 
Hope you can help.

bad news, friend...

[http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=557259](http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=557259)

> Date: Fri, 20 Nov 2009 20:00:01 UTC
Severity: grave
Found in version gnome-games/1:2.28.1-1
...
Subject: Clutter error in some games.


no fix for it out yet that i see. but, they rate it's severity as 'grave', and it was only first reported a few weeks ago... so hopefully a fix comes soon.

---

### Post by Skeezics on 2009-12-12
Oh well, I guess I will just have to wait.  Thanks for the info.

---

