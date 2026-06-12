---
title: "DBus message sent on connecting and external display?"
date: 2010-03-16
forum: General Help
---

### Post by ekspiulo on 2010-03-16
I can not find documentation concerning this Anywhere.  I'd like to write a script to listen to D-Bus for a signal indicating that an additional monitor has been connected to the VGA out, so the script can run xrandr and so forth.

I asked folks in #xorg-devel about D-Bus signals for a connection on the VGA port, and they told me that it probably involves udev and is probably graphics driver specific. In my case, I'm using an intel integrated graphics chip. Has anyone else done any video output port activity detection over D-Bus?



Thanks!

---

