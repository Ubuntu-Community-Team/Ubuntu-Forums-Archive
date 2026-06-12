---
title: "dbus-daemon RAM leak"
date: 2011-03-16
forum: General Help
---

### Post by theluddite on 2011-03-16
The process dbus-daemon gradually uses more and more RAM over the course of several days.  In the last 24 hours it's gone up by 20% and will eventually max out my RAM by using over %50.  How can I either:  a.  fix what appears to be a buggy process; or b.  figure out what may be using this process that is causing the memory leak so I can stop running it.

I initially thought it was dropbox, but not running it at startup didn't seem to help.  Maybe Transmission?  Conky?  Avant-window-navigator?  Compiz?  Firefox or a firefox plugin?  Rhythymbox? That's pretty much all I've got running in the background constantly.  Has anyone else had this problem with Maverick?

---

### Post by theluddite on 2011-03-19
So I figured out that this is happening on two of my four systems running Ubuntu.  So it rules out transmission, dropbox and skype.  I'm thinking it could be a conky script or a firefox plugin.  I guess I'm just going to try leaving these processes open one-by-one over the course of next week and see what causes the RAM leak.

---

