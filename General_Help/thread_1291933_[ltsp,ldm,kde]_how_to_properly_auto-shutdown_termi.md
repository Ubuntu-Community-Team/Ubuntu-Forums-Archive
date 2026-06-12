---
title: "[ltsp,ldm,kde] how to properly auto-shutdown terminal station?"
date: 2009-10-15
forum: General Help
---

### Post by qmax on 2009-10-15
using either /sbin/halt directly, or through switching to runlevel 0 - 
will not close x-session on server, and all related processes remain stale.
for gnome DE, there is workaround using watchdog.
but what to do in case of kde?

is there a way to make station close x-session ?

---

### Post by justleen on 2009-10-15
```
sudo /etc/init.d/gdm stop
```

will stop X (if you use GDM anyways..)

---

### Post by qmax on 2009-10-16
ubuntu distribution uses LDM on ltsp.
and it misses any ldm shutdown script.

and yes, terminating ldm process by pid closes session.

i guess it is a bug in distribution and should be filed somewhere.

---

