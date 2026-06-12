---
title: "Karmic Upstart: at what point are /var/lock and /var/run mounted"
date: 2009-11-25
forum: General Help
---

### Post by philipp2084 on 2009-11-25
Hi, 

Does anyone know at what point during the boot process /var/lock and /var/run are mounted? I presume it must be one of the first things that happens when upstart is called, yet I cannot find it in /etc/init (which is where all the upstart scripts are).

Neither can I find it in any of the scripts that are called at variolus runlevels. 


I would like to find this out since I would like to mount the whole of var as a tmpfs filesystem, rather than /var/lock, /var/run & /var/log as seperate ones.

---

### Post by markdv on 2009-12-03
This appears to be a well guarded secret. Every post asking the same/similar question I've seen seems to go unanswered. And I can't find it either...

Anyone?

---

### Post by jegerjensen on 2009-12-03
On hardy it seems to be done by the script /etc/init.d/mountkernfs.sh

---

### Post by markdv on 2009-12-03
> **jegerjensen said:**
> On hardy it seems to be done by the script /etc/init.d/mountkernfs.sh

In karmic there is no such script. There are scripts that _unmount_ the directories on shutdown, but not the mounting on startup. I've grepped through the better part of my installation and  even unpacked the initrd trying to find what is responsible for the mounting....  Frustrating....

---

