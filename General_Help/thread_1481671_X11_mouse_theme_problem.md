---
title: "X11 mouse theme problem"
date: 2010-05-12
forum: General Help
---

### Post by wigglestix on 2010-05-12
When i install a mouse theme via appearence setings it only works in firefox and other applications.The theme does not work on my desktop and other various places.I have viewed other threads regarding this error and the only fix would be to change the mouse theme in ccsm but fore some odd reason i do not have the option to change mouse themes in ccsm, i have looked everyware in ccsm and i can not find anyware to change the mouse theme?

---

### Post by wigglestix on 2010-05-17
Bump

Any help is appreciated I have tried many times to figure this out with no luck

---

### Post by maresee on 2010-05-18
Hey man, if you find solution for this please write it. Im haveing the same problem!

---

### Post by wigglestix on 2010-05-18
> **maresee said:**
> Hey man, if you find solution for this please write it. Im haveing the same problem!


Just wondering are you able to find the cursor options in compiz??

---

### Post by stinkeye on 2010-05-19
Solution here:
[**_[COLOR="DarkRed"]http://ubuntuforums.org/showthread.php?t=1475246&page=2[/COLOR]_**]("http://ubuntuforums.org/showthread.php?t=1475246&page=2")

---

### Post by wigglestix on 2010-05-19
> **stinkeye said:**
> Solution here:
[**_[COLOR=DarkRed]http://ubuntuforums.org/showthread.php?t=1475246&page=2[/COLOR]_**]("http://ubuntuforums.org/showthread.php?t=1475246&page=2")


Yes! This worked i opened the "x-cursor-theme" file in /etc/alternatives
using the command "**sudo gedit /etc/alternatives/x-cursor-theme**" and changed the line "**Inherits = themename" **to **"Inherits = ComixCursors-Orange-Large"(or whatever theme you wish to use) **then saved the file and rebooted.

---

### Post by intralot on 2010-12-15
change usr/share/icons/default/index.theme
then
in ccsm general properties. change the name of cursor theme with your theme name..thats it

---

### Post by wigglestix on 2010-12-15
Lol buddy this thread has been closed for a while;)

---

