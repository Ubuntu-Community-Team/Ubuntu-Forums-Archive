---
title: "Docky leaves odd &quot;ghosting&quot; after animations"
date: 2011-04-01
forum: General Help
---

### Post by gradysghost on 2011-04-01
This started yesterday.  I don't recall doing any updates that would be related to this problem.  Logging out and rebooting do nothing.

Okay, the problem:

I have a large monitor, so I generally keep Docky running without hiding at the bottom of my screen.  Yesterday, all animations now leave "ghosts" behind.  That is, the region Docky occupies doesn't get cleared between animation frames.

For example, as I hover over Docky, it zooms in on the icons.  When I move the mouse away, it all shrinks back down, but the remains of those frames stick around in that bottom 100 pixels or so.  This effect also takes place if I move from one desktop to the other (I have Desktop Wall enabled) and if I drag a window around in the Docky region.  This is really hard to describe, so I've attached a screencap.

My "About" screen cites this version:

Docky 2.0.13
bzr docky r1451 pre-release

I've got the Stable PPA imported right now, so I could possibly solve this problem by downgrading, but if I do that, some of my docklets will disappear, and that's not ideal.  Still, I'll try it and report back.  I'll also try and get some debug info out of Docky.  In the meantime, any suggestions on how to fix this would be greatly appreciated.

---

### Post by gradysghost on 2011-04-01
Ran `docky --debug` on a terminal, reproduced the problem, yet got no additional output in stdout.  No errors, just standard data coming from Docky and the docklets.

---

### Post by gradysghost on 2011-04-01
I "downgraded".  I went into /etc/apt/sources.list.d and commented the deb lines out of the two repo source files.

```
sudo apt-get remove --purge docky
sudo apt-get update
sudo apt-get autoclean
sudo apt-get autoremove
sudo apt-get install docky
```

The autoclean and autoremove commands removed quite a bit of stuff, most importantly the python-docky package.  After the reinstall, I have a slightly different version of Docky:

Docky 2.0.6

Yet the problem persists.  What are the odds that this is actually an X thing or a Python thing or a Mono thing?

---

### Post by gradysghost on 2011-04-01
Since reverting to the non-PPA version of Docky didn't solve the problem, I've reverted to the PPA version:

Docky 2.0.13
bzr docky r1451 pre-release

Any help at all would be greatly appreciated.

---

