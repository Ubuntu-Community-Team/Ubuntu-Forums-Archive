---
title: "how to use compiz  with xfce4 in ubuntu 11.10?"
date: 2011-11-28
forum: General Help
---

### Post by techvish81 on 2011-11-28
how to use compiz  with xfce4 in ubuntu 11.10?

---

### Post by Ra'anan on 2011-11-28
you need to load compiz, with 

compiz --replace ccp 

and add that to your start up scripts.

you can also use unity with xfce if you didn't know... same idea, add unity-2d-launcher as a command to your start up scripts...

you may want to remove xcompmgr if you have it

careful if you have already run compiz in a terminal before adding the scripts as the session manager will save that instance and you may end up running 2 compiz programs.

---

