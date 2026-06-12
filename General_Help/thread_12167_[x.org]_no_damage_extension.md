---
title: "[x.org] no damage extension"
date: 2005-01-22
forum: General Help
---

### Post by StefanFlan on 2005-01-22
I'm running ubuntu hoary with xorg 6.8 and when i'm trying to launcg xcompmgr(hey, i like eyecandy :oops: ) it comes with an error like:
```
No damage extension
``` 
and nothing happens.... did some googling, but i didn't find anything of any use...
i did a
apt-get --reinstall xorg
but it didnt help... does anyone know how to handle this problem? I have the ATI-drivers installed...

---

### Post by jensyt on 2005-01-22
From what I remember, when you apt-get install xcompmgr it also gets the necessary damage files...

Either way, if you're using the newest ATi drivers and get it to work (xcompmgr) can you explain it to me? I haven't been able to get xcompmgr to work with OpenGL support at the same time, nor does xcompmgr seem to work at all, really...

---

### Post by getaceres on 2005-02-01
[QUOTE=StefanFlan]I'm running ubuntu hoary with xorg 6.8 and when i'm trying to launcg xcompmgr(hey, i like eyecandy :oops: ) it comes with an error like:
```
No damage extension
``` 
and nothing happens.... did some googling, but i didn't find anything of any use...
i did a
apt-get --reinstall xorg
but it didnt help... does anyone know how to handle this problem? I have the ATI-drivers installed...[/QUOTE]
 I have installed the ati-drivers too and I get the same message.
I just installed today xorg in debian unstable (I'm thinking in change to ubuntu but I don't want to let kde) and the ati drivers. Then I installed xfce 4.2 enabling composite manager. 
I didn't get it to work on xfce so I used xcompmgr only to see that.
I have libxdamage1 and libxdamage1-dev installed. I don't know what's wrong. Maybe the ati drivers?

---

### Post by getaceres on 2005-02-01
It IS a problem with the fglrx drivers. Using the radeon driver I get shadows in xfce and I can use xcompmgr (but it's very very slow).
Next time I'll buy a nvidia card.

---

