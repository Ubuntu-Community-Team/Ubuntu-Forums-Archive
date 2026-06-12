---
title: "Out of swap space after recovery from hibernation"
date: 2011-06-16
forum: General Help
---

### Post by misha1983 on 2011-06-16
Sometimes my laptop (Asus K42Jr, Ubuntu 11.04) recovers from hibernation with almost zero remaining swap space.  It's almost completely unresponsive.  I can tell there is no swap remaining from looking at the system monitor applet.

Sometimes I can solve this problem by dumping the cache tables:

[HTML]sync; echo 3 > /proc/sys/vm/drop_caches[/HTML]

but that requires opening a terminal window, which can literally take minutes.  Usually I just run out of patience and power cycle the machine (which really defeats the whole purpose of hibernating).

I have 4GB of RAM, and 3.8GB swap space.  My RAM usage at the time of hibernation never exceeds 1GB.

What can I do to prevent this from happening?  A good start would be recovery with a completely empty swap.

---

