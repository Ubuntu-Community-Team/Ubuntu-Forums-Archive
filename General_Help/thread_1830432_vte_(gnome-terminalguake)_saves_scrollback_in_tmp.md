---
title: "vte (gnome-terminal/guake) saves scrollback in /tmp"
date: 2011-08-21
forum: General Help
---

### Post by BeniBela on 2011-08-21
Sometimes vte creates temporary files which contains a copy of the whole scrollback buffer, like:

gnome-ter 12915     user   40u      REG                8,1     5616   10064027 /tmp/vteH39M0V (deleted)


Is it possible to disable that (in the source if necessary)?  I work with sensible data which must not be written on the hard drive.

---

