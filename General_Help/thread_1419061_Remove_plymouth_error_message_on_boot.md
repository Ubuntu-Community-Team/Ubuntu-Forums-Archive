---
title: "Remove plymouth error message on boot?"
date: 2010-03-01
forum: General Help
---

### Post by scottbot84 on 2010-03-01
Hi all,

I'm running Lucid on my thinkpad sl510 with an intel ssd. I uninstalled plymouth since it seems to boot much faster without it(~ 14s w/ POST). However it is still giving me a small error message, "mountall: cannot connect to plymouth" other than that it boots normally.

Its more of an annoyance than anything, but I was wondering if anyone else who prefers a simple console boot would know how to get rid of this message. I assume its a line or two in an init script I need to comment out, but I can't seem to find it.

---

### Post by teh603 on 2010-03-01
Gotta second the much faster boot time without Plymouth. It seems to shave as much as 30 seconds off my boot time. The error message is a hair annoying, though.

---

### Post by OliverN on 2010-03-15
bump

maybe the question should be how you restore whatever stuff is going on between grub and gdm. some [COLOR="Navy"]sudo apt-get install --reinstall[/COLOR] command, presumably.

---

