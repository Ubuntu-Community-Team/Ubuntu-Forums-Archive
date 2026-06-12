---
title: "fixed screen flicker"
date: 2010-02-18
forum: General Help
---

### Post by shadowcrunch on 2010-02-18
Hello! I'm posting a potential solution to an annoying problem I had, so if I'm in the wrong spot, please let me know or maybe a mod can move the post or something. Oh, and I say potential solution because it worked for me, but it may not work for anyone else. 
I'm running 9.1 Karmic (32-bit) on an Athlon64 X2 4000+, and my graphics cards is an ATI Radeon X1600 (using the stock drivers that installed from the ubuntu install disc). Oh, and my monitor is a ViewSonic 19" VA912b.

Problem was one day the screen started flickering to black while I was on the web. Like hitting the power switch type of black. Might do it once, might do it 8 times, always at random times whether I had a program open or just staring at the desktop. I started trying to backtrack any changes I made graphically, like resizing my bottom panel or turning on opacity in compiz. This went on for a few days.

Finally I remembered I had installed a game that crashed to desktop as soon as I started it, but it had changed the desktop resolution and it got stuck at the new (smaller) resolution. When I went in to change it back, I noticed my refresh rate had been changed from 60 to 70 hZ, which I thought was odd because when I installed ubuntu 60 was my only option. When I found it, I figured it's faster, so leave it alone. Well, two days ago I went into "System>Preferences>Display Preferences" and reset the refresh to 60 hZ, and I haven't had a flicker since. 

Sorry if this problem has been covered before. I couldn't find anything searching the forums or google, so I figured I would put the info out there. Hope it helps someone!

---

