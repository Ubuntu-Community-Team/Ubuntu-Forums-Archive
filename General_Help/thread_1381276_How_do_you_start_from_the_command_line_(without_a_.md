---
title: "How do you start from the command line (without a GUI)"
date: 2010-01-14
forum: General Help
---

### Post by Bre Ntt on 2010-01-14
How do I set it to where there is no GUI (i.e. GNOME) on startup? I want only bash to run on startup. 

Also, what is the command to start Gnome? Is it just gnome?

I tried to ask this question in Desktop Environment, but its been a while, several views and nobody has given an answer. Is there not a way to do it in Ubuntu?

---

### Post by ThePickleMan on 2010-01-14
See this thread: [http://ubuntuforums.org/showthread.php?t=66420](http://ubuntuforums.org/showthread.php?t=66420)
Several Solutions are posted.

---

### Post by Leppie on 2010-01-14
you can edit the gdm.conf to something like this:
```
start on (runlevel [345]
          and filesystem
	  and started hal
	  and tty-device-added KERNEL=tty7
	  and (graphics-device-added or stopped udevtrigger))
stop on runlevel [0126]
```
like this, in runlevel 2 (default runlevel in ubuntu) gdm won't start and switching to runlevel 2 will kill the x session.

---

