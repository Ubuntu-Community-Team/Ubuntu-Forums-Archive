---
title: "Long disk I/O pauses with SSD AspireOne on Karmic"
date: 2009-11-17
forum: General Help
---

### Post by JohnTheLutheran on 2009-11-17
I recently upgraded from Jaunty to Karmic on my Acer AspireOne model ZG5 with 16GB solid-state hard-drive. 

Ever since then, I've noticed a significant increase in disk I/O. The problem with this is that (since the SSD on the ZG5 is notoriously slow) this results in the whole computer becoming unresponsive for several seconds at a time, which seriously impairs user experience. 

Is there a way to find out what's causing the increased disk I/O and to reduce it? Actions already taken when I installed Jaunty: 
[LIST]
[*]Root and /home filesystems mounted noatime
[*]/tmp mounted as a RAM disk
[*]Firefox using the /tmp folder for caching
[/LIST] 
Any other tips would be very welcome.

---

### Post by P4man on 2009-11-17
try running ```
iotop
``` from the terminal to see whats causing it. May have to install it first, its in the repo's.

---

### Post by JohnTheLutheran on 2009-11-20
Thanks, will give that a try (sorry for delay in responding - hadn't subscribed to this thread!).

---

