---
title: "view daemons and services"
date: 2006-05-15
forum: General Help
---

### Post by alistair77 on 2006-05-15
How can I view the state of daemons and services?  Equivalent of rc-update show in Gentoo?

---

### Post by tonyr on 2006-05-15
Several possibilities to look at:
[LIST]
[*]package **sysvconfig**   (contains **service**)
[*]package **sysv-rc-conf**
[*]package **rcconf**
[/LIST]

**sysv-rc-conf** and **rcconf** provide **curses** based interfaces. 
**sysv-rc-conf** puts all of the run levels right there in the display. 

The **Gnome** utility is **System->Administration->Services**. The KDE
utility is **Kmenu->System Settings->Services** (or maybe it's **System Services**).

There is also a package named **Bum** (**B**oot**U**p **M**anager)
that provides a GUI to service/daemon management.

I haven't seen **chkconfig** around here in a while, but that doesn't mean  that
it isn't here somewhere.

---

### Post by tonyr on 2006-05-15
Oops, missed one.  Package **sysv-rc-conf** also provides **update-rc.d**
for managing services start/stop and run levels.  It doesn't seem to have
a **list** option, though.

EDIT:  ...and I don't think **chkconfig** is in Ubuntu at all; lot's o'
threads and articles around bemoaning this fact.

---

