---
title: "Sound Problems in Karmic Koala"
date: 2009-11-30
forum: General Help
---

### Post by techmn on 2009-11-30
I have installed Karmic Koala on my Toshiba Tecra Tablet PC. So far the only problem that I have been having is with my sound. Now I did upgrade from the previous version of ubuntu so this is not a fresh install, however I don't know if this actually matters with linux like it sometimes does with windows. The problem is that sometime I have sound and sometime I don't. When I boot the system, if I get sound at the logon screen, I don't get it when it fully loads the user settings in my user account. Now sometimes when I don't get the sound at the logon screen, I will get it when it fully loads in the user account, but then again sometimes I don't get it at all. It seems that something may be conflicting with the driver but I don't know how to check this. I did not have any problems with the sound in the previous version. Maybe if a new driver is released for the sound chipset it will fix this problem but I would like to attack this problem now and see if I could come up with a solution, I just need some help pointing me in the righ direction to start checking things. Any ideas?
Thanks.

---

### Post by Favux on 2009-12-02
Hi techmn,

Welcome to Ubuntu Forums!

First find out what your audio chipset is.  In a terminal enter:
```
aplay -l
```
That should give you something to search with.

Hope this helps.

---

