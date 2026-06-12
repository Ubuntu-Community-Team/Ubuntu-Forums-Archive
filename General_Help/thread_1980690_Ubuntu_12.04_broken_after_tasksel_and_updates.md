---
title: "Ubuntu 12.04 broken after tasksel and updates"
date: 2012-05-15
forum: General Help
---

### Post by kabeza on 2012-05-15
Situation

- clean Ubuntu 12.04 install. All was fine, no video problems
- was downloading 296mb of updates, but cancelled download to install lamp
- installed tasksel, then lamp, and all went fine
(at this time, theme changed and "old-default" was set)
- rebooted PC
- never started again

Now this install doesn't start properly, it gets stuck at some "battery" message [OK] and only can login at tty

I've started with right shift at grub menu, then repair mode, and then chose the repair damaged packages

**What else should I do to recover the working installation?**

PS: Ubuntu plymouth shows with text-font, not image

**Can this be a video problem? WT* has tasksel related to video problems?**

---

### Post by rai4shu2 on 2012-05-15
It might be something you can fix with:

```
sudo apt-get install ubuntu-desktop
```

That's just a wild guess, though.

---

### Post by kabeza on 2012-05-16
> **rai4shu2 said:**
> It might be something you can fix with:

```
sudo apt-get install ubuntu-desktop
```

That's just a wild guess, though.


Is there any option I could install ubuntu-desktop packages from the liveCD?... there's no way I will be able to download 250mb at this hour (4kb/s)

---

### Post by rai4shu2 on 2012-05-16
I don't suppose you could save the contents of /var/cache/apt/archive somewhere, then clean install and later restore the contents of that folder? That would expedite matters a little, I think.

---

