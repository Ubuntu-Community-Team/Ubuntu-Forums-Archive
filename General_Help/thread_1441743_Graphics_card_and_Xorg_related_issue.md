---
title: "Graphics card and Xorg related issue"
date: 2010-03-29
forum: General Help
---

### Post by belnac on 2010-03-29
Hi,

Since I started using Ubuntu I noticed Xorg was taking up quite a lot of cycles to do easy tasks like move/resize window, etc. I investigated a little on the net and eventually found a way to solve it, which requires adding the following line to xorg.conf in the Device section:

```
Option "MigrationHeuristic" "greedy"
```

Now, that change alone made Xorg super fast - awesome -  *but* I'm now getting a 1.5-2s delay when maximizing/restoring windows. I know for sure it's the line above which was added to xorg.conf that is causing this behaviour, as I've reverted back to the original settings and the delay was gone (and Xorg was slow again lol.)

Would appreciate some help in fixing this or at least minimizing the delay. Thanks!


EDIT: Graphics card is ATI X700 Mobility; Xorg using opensource ati driver.

---

