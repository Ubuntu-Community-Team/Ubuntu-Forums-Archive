---
title: "Ethernet crossover between two machines"
date: 2010-07-11
forum: General Help
---

### Post by spazzeri on 2010-07-11
Using wicd 1.7 in ubuntu karmic and a crossover ethernet cable linked to another machine, all I needed for the network between the two machines to go up was to click 'Connect' on the wicd GUI: it assigned a 169.254.* IP address to the ubuntu machine (like the other one). And with avahi-daemon running, life was good.

Since I upgraded to ubuntu lucid, this no longer works ("Unable to get IP address").
What kind of networking configuration should be tweaked to make that work again -- possibly without leaving wicd ?

---

