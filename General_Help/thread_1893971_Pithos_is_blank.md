---
title: "Pithos is blank"
date: 2011-12-11
forum: General Help
---

### Post by Umunthu on 2011-12-11
I installed Pithos 0.3.13, but the interface is completely blank and silent. I can log in to Pandora without problems, and I haven't gotten any error messages whatsoever.

[ATTACH]208914[/ATTACH]

---

### Post by Umunthu on 2011-12-12
Anyone?

(I hope I'm not violating a bumping rule.)

---

### Post by gar37bic on 2012-01-09
This appears to be happening to me too, sometimes.  I'm running 0.3.14, Ubuntu 10.04 (lucid), kernel 2.6.32.-37-generic, Gnome 2.30.2 (and compiz with cairo-dock).  I ran some tests this morning.  When first started from the Ubuntu menu, it basically stalled at the 'Logging in' phase.  But when I started from the command line with 'pithos --gst-debug-level=2', it started fine.  And after that, it started just fine with just 'pithos', and also now starts just fine (albeit a bit slower than previously) from the menu.  Strange.

---

### Post by gar37bic on 2012-01-09
I've posted a bug report at [https://bugs.launchpad.net/pithos/+bug/913969](https://bugs.launchpad.net/pithos/+bug/913969) as well.

---

