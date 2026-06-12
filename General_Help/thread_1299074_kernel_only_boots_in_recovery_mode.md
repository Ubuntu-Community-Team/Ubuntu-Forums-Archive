---
title: "kernel only boots in recovery mode"
date: 2009-10-23
forum: General Help
---

### Post by incognito1 on 2009-10-23
I have one kernel installed on my machine, but for some reason it will only boot in recovery mode and not normal mode. I think the problem is related to the stuff i added into /etc/fstab, namely noatime,data=writeback. I did a bit of research and I thought maybe it was initrd but then recovery mode probably shouldn't work. 

In normal mode i get this error:

exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x2 frozen

And boot up halts.



Greatly appreciate if someone could help me figure this out.

---

### Post by running_rabbit07 on 2010-01-07
Boot the older kernel and run the update manager to install the newest kernel. Or, reinstall.

---

