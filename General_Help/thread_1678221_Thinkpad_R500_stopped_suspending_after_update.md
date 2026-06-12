---
title: "Thinkpad R500 stopped suspending after update"
date: 2011-01-30
forum: General Help
---

### Post by metalball on 2011-01-30
Hey all,
my thinkpad stopped suspending for some reason,
when i'm trying to suspend some weird message pops out
```
Invalidating stale software suspend images...
```
and im simply goes to lock screen mode.

i've tried to install suspend2, didn't help,
tried some fix i've read about USB3
> echo blacklist xhci_hcd | sudo tee -a /etc/modprobe.d/blacklist.conf >/dev/null
didn't help either.

Running Ubuntu 10.10

---

### Post by metalball on 2011-01-30
bump):P

---

### Post by metalball on 2011-01-30
update: when booting Ubuntu with 2.6.35-24 Kernel instead of 2.6.35-25 suspend works!

---

