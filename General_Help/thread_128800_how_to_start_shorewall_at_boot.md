---
title: "how to start shorewall at boot?"
date: 2006-02-12
forum: General Help
---

### Post by shams2 on 2006-02-12
hi,
i installed the shorewall, how i cant start it with system boot?

---

### Post by evs on 2006-02-12
Shorewall is not a daemon, so it does not run at boot.  It actually configures Netfilter, so if you make any changes to the Shorewall configs, just type ```
/etc/init.d/shorewall restart
``` and it will configure Netfilter accordingly, and then stop executing.

---

### Post by shams2 on 2006-02-12
thanks for reply, is it mean when i start my system i will start shorewall manually? i am new to ubuntu, in fedora i put the shorewall in runlevels 3,4,5 with chkconfig so at boot shorewall was started from /etc/rc.d/init.d/shorewall and there was message at boot starting shorewall  [OK] that means shorewall started, but in ubuntu don't know how add shorewall in runlevels and how to check the runlevels?

---

