---
title: "Spin down HDDs works in Fedora, doesn't in Ubuntu"
date: 2011-02-12
forum: General Help
---

### Post by t1497f35 on 2011-02-12
Hi,
This option (see screenshot) in Ubuntu (10.10 64bit) doesn't work, the other HDD just never spins down.
In Fedora 14 32bit on same computer it does work.

Is there any easy way to fix this in Ubuntu?

---

### Post by mikewhatever on 2011-02-12
Try checking the timeout setting in gconf-editor, /apps/gnome-power-manager/disks. The default AC timeout in Ubuntu is 600 seconds. Compare it to that of Fedora or, perhaps, lower it just to see if it makes any difference.

---

### Post by t1497f35 on 2011-02-14
Thanks, tried, unfortunately didn't fix the issue.. in case it matters here's my hardware specs (sudo lshw >> file.txt)

---

