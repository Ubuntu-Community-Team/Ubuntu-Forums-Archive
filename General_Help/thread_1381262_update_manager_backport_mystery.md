---
title: "update manager backport mystery"
date: 2010-01-14
forum: General Help
---

### Post by vientito on 2010-01-14
I have logged in today and update manager reminds me of an update with linx-backports-module-2.6.31-14-generic.  However my current kernel has been updated a while ago and is now 2.6.31-17.  That obviously is more recent that that backport version.  What should i do?  By the way that update is from a PPA repository other that the default.  

I am wondering the update manager has no way to tell which kernel version i have at all?

Should i actually go ahead with the installation?

---

### Post by ajgreeny on 2010-01-14
If you have not uninstalled the 2.6.31-14 kernel, any updates to it will still be notified to you, even though you are not using it any more.

If you have already updated your kernel to 2.6.31-16 or 2.6.31-17, you can either ignore this -14 update or just remove all the packages relating to 2.6.31-14 completely.

Just remember that it is always worth keeping one older kernel after an update, just in case your current one goes wrong for some reason.  You will then have a working kernel to fall back on.

---

