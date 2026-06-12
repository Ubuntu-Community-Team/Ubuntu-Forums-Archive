---
title: "freezing - please help!"
date: 2009-12-26
forum: General Help
---

### Post by daves111 on 2009-12-26
after installing ubuntu 9.10 desktop-64, in gnome, my computer freezes after loading the desktop; usually after I move the mouse to click on something. I've used ubuntu for over a year and it worked fine until I upgraded to 9.10. It will run in failsafe gnome without freezing.

so far, I have ...
I replaced my hardrive (I think it was getting weak) from 160gb to 500gb
made a cd with iso on it (I did hash check and verified cd was good) but ... same problem. 
tried to get help on irc
tried a different mouse

computer is ...
compaq presario ts-xn0105rs
it was advertised as celeron D 360 3.46 GHz "64-bit processor" (system says celeron D 3.46)
1.5gb memory

when I installed, I let ubuntu have whole drive

---

### Post by MooPi on 2009-12-27
type in terminal ```
sudo lshw
```The first thing listed should be the specs on your CPU. It should show 64bit just to check. But I don't think the system would have installed if it weren't.

---

