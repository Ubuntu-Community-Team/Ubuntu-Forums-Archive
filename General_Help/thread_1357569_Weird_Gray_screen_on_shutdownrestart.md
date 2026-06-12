---
title: "Weird Gray screen on shutdown/restart"
date: 2009-12-17
forum: General Help
---

### Post by mbuller10 on 2009-12-17
Okay so here's the deal, after the newest kernel upgrades on Karmic, something happens randomly. It's kind of hard to describe but I will get this screen with all of these little grey rectangles on it, that kinda shift to the right slightly and then ubuntu shuts down. During one of my boot up's after having this error I got an error saying that nvidia drivers failed to load. I also always get a lot of flickering on boot up. I'm guessing this is an nvidia problem. I have a thinkpad sl500 with an nvidia geforce G 105M 256 mb graphics car and the 190 drivers. It happened even more on the 185 drivers. I am running compiz and i would strongly prefer not to disable it.

---

### Post by dcstar on 2009-12-17
> **mbuller10 said:**
> Okay so here's the deal, after the newest kernel upgrades on Karmic, something happens randomly. It's kind of hard to describe but I will get this screen with all of these little grey rectangles on it, that kinda shift to the right slightly and then ubuntu shuts down. During one of my boot up's after having this error I got an error saying that nvidia drivers failed to load. I also always get a lot of flickering on boot up. I'm guessing this is an nvidia problem. I have a thinkpad sl500 with an nvidia geforce G 105M 256 mb graphics car and the 190 drivers. It happened even more on the 185 drivers. I am running compiz and i would strongly prefer not to disable it.

It is either a graphics driver issue or a splash screen issue.

Install the **startupmanager** package and have a play with the resolution options.

---

### Post by mbuller10 on 2009-12-18
thanks man it was the resolution in usplash, i couldn't figure out the right setting so i just uninstalled usplash

---

