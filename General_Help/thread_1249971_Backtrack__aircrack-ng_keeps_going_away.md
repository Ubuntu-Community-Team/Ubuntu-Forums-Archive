---
title: "Backtrack:  aircrack-ng keeps going away"
date: 2009-08-26
forum: General Help
---

### Post by t0p on 2009-08-26
I've been playing with Backtrack 4 (pre final) live usb on my EeePC.  In particular, I've been using aircrack-ng to try cracking a WEP router.  And this weirdness keeps happening: I've got aireplay-ng (I think) and airodump-ng running, collecting IVs.  When I've got a nice number of them, I launch aircrack-ng to try and crack the key, while airodump-ng is still collecting IVs.  After a short while, the screen goes black and the mouse pointer won't move.  Nothing I do can make it work.  So I have to do the SysRq-REISUB thing, with the result that I lose all the IVs I collected and have to start again.  Though I don't know why I bother as the same thing happens again.

This isn't a monitor power-saving thing - I always make sure I turn off power-saving before I start, and anyway it happens even if I'm actively using the touchpad/keyboard.  I'm baffled at this behaviour.  Anyone know what's going on/how I can prevent it?

---

### Post by t0p on 2009-08-28
I'm bumping this cos it's had no replies since I posted it **2 days ago**!!! And also to pose a question (which may be the answer I seek... but which in turn poses another question).

This is happening when I'm using a **live usb** of Backtrack, when airodump-ng is sucking packets out of the ether and writing them to a file on the root desktop - ie, as it's a live session, the file is actually being written to RAM.

Now, I'm using an Eee PC with 512MB RAM.  Could this problem - the screen going black and the mouse pointer freezing - be due to the RAM running out?  See, I don't know if running out of RAM could cause such symptoms.  Also, I don't know how many data packets it would take to fill 512MB of RAM.  But I must be grabbing several hundred thousand at least before all goes dark.

So, is this down to RAM running out?  And has anyone got a suggestion for a fix?  (Apart from getting more RAM.  I'm gonna get a couple of gigs next week, but it would be cool if there's something I can do in the meantime that doesn't involve spending money)

---

