---
title: "system hangs on boot when stating samba daemons"
date: 2010-02-07
forum: General Help
---

### Post by Zidaps on 2010-02-07
Hi,

My system was working fine. I followed a thread online to try to get samba to share better, installed "winbind" and now I can't get passed "Checking System Files" on boot up.

Upon boot, "Checking System Files":
  Starting Firestarter firewall  ....  fails.
  Starting samba daemons _    ....  Just hangs there forever :(

Is there a way to get back into my system so that I can uninstall winbind, firestarter, or samba if need be??

---

### Post by Zidaps on 2010-02-07
Issues solved,

Booted with a live cd. mounted file system by going to:
Places >> drive

opened terminal: gksudo nautilus
went to, and opened file system:
/media/disk

Once in there, removed the samba file as well as the winbind file from:
/etc/init.d

Restarts like brand new. :D

---

