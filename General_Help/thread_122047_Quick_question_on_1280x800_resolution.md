---
title: "Quick question on 1280x800 resolution"
date: 2006-01-26
forum: General Help
---

### Post by stanleys on 2006-01-26
I know about the 855resolution guide, and I've used the [ instructions in this thread before.]("http://www.ubuntuforums.org/showthread.php?t=24923&highlight=855resolution")
Just recently I did a fresh install of Ubuntu, and I noticed that 855resolution is now listed in Synaptic Package Manger.
Then I went back to that thread and noticed that some are having problems with fonts not being the right size.

Since this is a fresh install, I need to configure the resolution again - but is there a newer way to get this done? should I do it through Synaptic?

---

### Post by joehill on 2006-01-26
I just edited my /etc/default/855resolution file to read:

MODE=58 #adjusted for the mode I wanted to replace
XRESO=1280
YRESO=800

The startup script in my installation was already in /etc/init.d/855resolution, so as soon as I restarted X, the changes were in effect.

---

### Post by stanleys on 2006-01-26
thanks joe. I did just that, restarted, and everything kicked in right away.
that was the exact answer I was hoping to get :)

---

