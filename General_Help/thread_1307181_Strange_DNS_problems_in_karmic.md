---
title: "Strange DNS problems in karmic"
date: 2009-10-30
forum: General Help
---

### Post by AussieGuy69 on 2009-10-30
Im having DNS problems after upgrading to karmic.
A fresh install wont work as ive already tried resolving the problems by "run ubuntu without modifying my machine" from the cd and get exactly the same problem.

Bascially, any GUI based program beleives google.com, irc.freenode.org and a number of other sites have the IP of 1.1.1.1.

Funnily enough however, console programs access the internet fine, my web server is accessible from the internet, links (console web browser) can open any website I type in.

Ive got my DNS etc set manually as per my networks hardware set-up.

Any idea on what might be causing this unusual problem?

-Aussieguy

---

### Post by AussieGuy69 on 2009-10-30
Update & Bump:

The problem appears to only affect GTK/Gnome apps (including Firefox), and KDE apps running under gnome e.g. konqueror.

Windows XP Running under Virtualbox on this system accesses any site I want it to, so im using it to access websites until karmic under gnome is working properly.
amsn (tcl/tk app) works fine also.


Something to do with gnome??? What could it be?

---

### Post by AussieGuy69 on 2009-10-31
Fixed this issue.

The problem was karmic installs ipv6.

ipv6 was causing all my problems.

Ive added the option to disable ipv6 to the grub boot line for mykernel and now everything works fine.

So if you have strange DNS problems like me after installing karmic, try this.

-Aussieguy

---

### Post by mechgt on 2009-11-08
Can you be a little more specific as to what you did?  I'm unfamiliar with the disable option

---

