---
title: "simulteneous use of multiple bluetooth dongles"
date: 2011-04-26
forum: General Help
---

### Post by angshu31 on 2011-04-26
Hi:
I am trying to scan for Bluetooth devices using multiple USB bluetooth dongles attached to a laptop to increase the probability of discovering devices faster.  However, when I run "hcitool -i hci0 scan" and "hcitool -i hci1 scan" simultaneously, the performance seems to degrade instead of improving.  In the two adapter scenario, more devices are "missed" than the in the one-adapter case.  Gives me the impression that both the devices are not running a scan simultaneously for some reason.  Is there some such limitation in the bluez stack, that prevents multiple bluetooth devices on a single computer from working simultaneously?

---

### Post by poppel92 on 2012-10-01
Hi angshu,

I am wondering if you solved this issue? I want to do an inquiry at two bluetooth adapters at the same time. 

Thanks,

JP

---

