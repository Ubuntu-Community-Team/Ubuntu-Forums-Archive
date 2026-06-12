---
title: "Upgrade from Recover mode 9.10"
date: 2010-09-30
forum: General Help
---

### Post by ajaydprabhu on 2010-09-30
Hi,

I have a problem with my XSERVER and the login screen does not load. I tried everything in all forums still no help. I usually get a message E: could not open file /var/lib/dpkg/status - open (2 no such file or directory). Xserver repair also failed.

Can some one suggest how to upgrade to 10.04 from the recovery console. I have the install CD and the alternate CD. 

When i put alternate cd and reboot i do not get option to upgrade
Also tried Alt+f2 and gksu "sh cdrom/cdromupgrade" i get a message like invalid command gksu or gksu not found. 

please help me to upgrade.

---

### Post by P4man on 2010-09-30
gksu is the graphical sudo, it requires a working xserver. From a command prompt use sudo. But im not sure the updater works without x.

---

