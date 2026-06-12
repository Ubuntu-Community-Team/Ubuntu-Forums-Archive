---
title: "ip_forward returing to previous state on reboot"
date: 2011-03-17
forum: General Help
---

### Post by nkae100 on 2011-03-17
I execute

> sudo echo 1 > /proc/sys/net/ip_foward

This command changes the 0 to 1, but returns to 0 once I reboot.


I've tried rebooting and dropping to a shell without networking as root and executing the same command, but still to no avail.


Does anyone know why is this occurring?

---

