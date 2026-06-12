---
title: "GDM segfaults a lot after update"
date: 2010-05-26
forum: General Help
---

### Post by VirusCollector on 2010-05-26
This just started today, after I installed a round of updates yesterday:

I would attempt to login to my GNOME session. One of three things happens: it hangs, looking like it's authenticating, it lets me into my session but then abruptly logs me out and wrecks anything I was doing, or GDM just crashes altogether.

On tty6, I found this error in dmesg:

```
gdm-session-wor[1392]: segfault at 1 ip 0000000000000001 sp 00007fff57babe18 error 14 in gdm-session-worker[400000 + 17000]
```

The numbers may be slightly off, I had no way to copy and paste the error. I have no modifications to GDM except libpam-usb, which doesn't even work. Is it possible to roll back GDM to before the update?

---

### Post by VirusCollector on 2010-05-27
It's amazing how quickly I can't even find my own thread anymore. Is any help coming?

---

### Post by dr770 on 2010-12-03
some using pamusb have had that problem.
if you are usuing it disable gdm in pamusb.conf

---

