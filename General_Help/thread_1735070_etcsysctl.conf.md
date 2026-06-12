---
title: "/etc/sysctl.conf"
date: 2011-04-20
forum: General Help
---

### Post by dctrsatan on 2011-04-20
How do I make a change to this file?  More specifically this is what I am trying to do.

Add the following line to /etc/sysctl.conf
vm.swappiness=10

---

### Post by deconstrained on 2011-04-20
You gotta have superuser permissions to edit anything in /etc

Alt-F2 gksudo gedit /etc/sysctl.conf

---

### Post by dctrsatan on 2011-04-22
Thank you it worked perfectly.

---

