---
title: "busybox 1.17.1"
date: 2011-04-16
forum: General Help
---

### Post by nigelreloaded on 2011-04-16
hi guys im new to ubuntu my computer just crashed and started booting at busybox i it wont load ubuntu anymore pls help.
using narwhal beta 2.

---

### Post by coffeecat on 2011-04-16
When the system crashed, was there a hard shutdown as well? Did you have to switch off the power to shut it down? A busybox shell can sometimes be a symptom of a corrupted filesystem, so a filesystem check would be the first thing to try.

Boot up with your Natty Beta2 live CD and open Gparted. Select the partition Natty is installed to and right-click. Select "Check" and click on the green "Apply" button.

---

