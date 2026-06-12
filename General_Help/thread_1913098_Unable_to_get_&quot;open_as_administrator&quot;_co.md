---
title: "Unable to get &quot;open as administrator&quot; context menu."
date: 2012-01-21
forum: General Help
---

### Post by techvish81 on 2012-01-21
Unable to get "open as administrator" context menu.

I installed nautilus gksu and gksu packages.

Still not getting that option in right click/ context menu.

---

### Post by mc4man on 2012-01-21
While nautilus-gksu is available in 11.10 it is installed in the incorrect location (was never rebuilt for use in gtk3
So with the package installed you need to copy, move or symlink it in the proper dir.
Ex. of copy command
```
sudo cp /usr/lib/nautilus/extensions-2.0/libnautilus-gksu.so /usr/lib/nautilus/extensions-3.0/

```
Then just restart nautilus or do a log out/in

---

### Post by techvish81 on 2012-01-22
> **mc4man said:**
> While nautilus-gksu is available in 11.10 it is installed in the incorrect location (was never rebuilt for use in gtk3
So with the package installed you need to copy, move or symlink it in the proper dir.
Ex. of copy command
```
sudo cp /usr/lib/nautilus/extensions-2.0/libnautilus-gksu.so /usr/lib/nautilus/extensions-3.0/

```
Then just restart nautilus or do a log out/in

thank you!!
it took under 10 sec.

---

