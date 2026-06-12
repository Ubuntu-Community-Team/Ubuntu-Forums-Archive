---
title: "Menu bar and Application launcher disappears."
date: 2011-05-16
forum: General Help
---

### Post by DeadlyBreakdown on 2011-05-16
I installed a new theme and my menu bar glitched. I restarted and when i boot up, there is no more menu bar or application bar (running 11.04) I boot into classic or safe mode and the bars are there. i already tried right click > change background > changed theme with no success. Any ideas?

---

### Post by DeadlyBreakdown on 2011-05-16
Fixed it. I simply reset the gnome. Sorry if this was a common fix, I'm new to linux.

```
rm -rf .gnome .gnome2 .gconf .gconfd 
```

---

