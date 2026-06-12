---
title: "Panel clock off by 3 - 6 hours, on alternate boots"
date: 2009-11-06
forum: General Help
---

### Post by DapperMe17 on 2009-11-06
Karmic Koala

Every other boot or so, I've noticed that my panel clock is ahead by 3, or 6 hours. Other boots, it's fine.

I do have 'ntp' installed, & allowed via firestarter. Time is set to be automatically updated via multiple servers.

Any ideas?

Solved......changed UTC to "yes" in /etc/default/rcS

---

