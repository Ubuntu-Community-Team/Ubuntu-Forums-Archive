---
title: "Plasma hangs, how I restart it"
date: 2009-07-10
forum: General Help
---

### Post by LightningCrash on 2009-07-10
Something I do hangs up Plasma all the time. Plasma hangs, taskbar quits, all plasmoids screw up. Pain in the butt.

Fortunately I still have Yakuake up, so I F12ed to it and started playing. If I restart GDM/KDM I lose my session, and I don't want that.

I tried `kquitapp plasma`, but it said it couldn't find plasma.
So, the solution I use:
pkill plasma
nohup kstart plasma

Ta-da!
Didn't have to nuke my session.
:guitar:

---

