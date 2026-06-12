---
title: "Loading modules with options"
date: 2011-04-04
forum: General Help
---

### Post by inso_741 on 2011-04-04
I want to load the nouveau module with "perflvl_wr=7777"
how do I do this? should I just add in /etc/modules?


Edit: adding "nouveau.perflvl_wr=7777" to the kernel command line works
although adding "nouveau --options perflvl_wr=7777" to the /etc/modules
and running update-initrmfs might also work...haven't tested

---

