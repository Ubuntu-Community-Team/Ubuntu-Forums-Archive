---
title: "1000 fps hlds"
date: 2010-03-05
forum: General Help
---

### Post by powerstubbs on 2010-03-05
Im currently running Ubuntu 9.10 (desktop 32bit)
 
I would like to know how to recompile my kernel so it runs at 1000Hz. This will for the purpose of an equal thousand FPS out of my HLDS (half life dedicated server). Can someone help me or provide a detailed walk through so I can recompile my kernel to run at 1000Hz? 
 
Im running Ubuntu (9.10 desktop 32bit)
 
hardware:
Two Xeon 2.8Ghz/HT CPUs 
3GB of RAM 
 
I am looking to run a 14 or 16 man public HLDS cs 1.6 server that has 1000fps even at full load.
 
thanks!

---

### Post by Paradox Uncreated on 2010-03-20
[http://translate.google.no/translate?js=y&prev=_t&hl=no&ie=UTF-8&layout=1&eotf=1&u=http%3A%2F%2Fwww.howto-cs16-root.de%2Findex.htm&sl=de&tl=en](http://translate.google.no/translate?js=y&prev=_t&hl=no&ie=UTF-8&layout=1&eotf=1&u=http%3A%2F%2Fwww.howto-cs16-root.de%2Findex.htm&sl=de&tl=en) (?)

---

### Post by asmoore82 on 2010-03-20
Would not FPS(?frames per second?) me more of a concern to the clients than the server?

---

### Post by DawieS on 2010-03-20
fps as in **Frames Per Second ?**

Even if the hardware and software was capable of those speeds, then your eyes would not be able to fully see more than about 10% of the frames, unless you are super-human.

1000 fps films are used to measure particle movement during explosions and bullet trajectories.:eek:

---

### Post by powerstubbs on 2010-03-20
> **DawieS said:**
> fps as in **Frames Per Second ?**
 
Even if the hardware and software was capable of those speeds, then your eyes would not be able to fully see more than about 10% of the frames, unless you are super-human.
 
1000 fps films are used to measure particle movement during explosions and bullet trajectories.:eek:
 
 Correct for games, but this is for a game server program that defines FPS for itself differently. FPS with regards to HLDS, is the speed at which HLDS.exe processes information between the its clients and itself. 1000Hz kernel allows for HLDS to run at "1000fps" which in return makes for a smooth responsive gaming experience for the players connected to it. :)

---

### Post by Paradox Uncreated on 2010-03-22
Yes, the most psychovisually minimal noise, is with ~72.586 FPS. (vsynced).

---

