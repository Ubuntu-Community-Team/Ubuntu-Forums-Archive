---
title: "Double clicking flash loses focus"
date: 2009-12-01
forum: General Help
---

### Post by crabbadon on 2009-12-01
It seems fairly unique that, in addition to the flickering which is new, I've had since maybe Jaunty the problem that double-clicking in Flash makes it lose focus. I've not found anyone else with this problem; do you know why it might be and what I might do?

---

### Post by Ruxias on 2010-02-18
I'm a bit surprised to see no one else has posted here yet. I was having this problem when I had Hardy installed on my laptop. I'm using Karmic now, and I'm still having the same issue. In both installations I was using the "adobe-flashplugin" package from the repositories.

This is most apparent in flash games. I didn't know if it was just clicking too fast or the double-click event that caused this, so I did a test. I found that reducing the double-click timeout in "System->Preferences->Mouse" to the lowest value helps this problem, obviously by making double-click require a really fast pair of clicks.

I'm hoping that this is something that can be easily fixed, but it seems most problems with flash just get a reply telling you to vote on the bug at adobe's bug tracker. I'm going to look around and see if I can find any useful information.

---

