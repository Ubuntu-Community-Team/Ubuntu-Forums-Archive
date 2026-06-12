---
title: "Does formatting automatically invoke TRIM on an SSD?"
date: 2012-09-25
forum: General Help
---

### Post by Asmodai on 2012-09-25
If I reformat a partition with ext4 using gparted, will gparted or the kernel automatically do a TRIM request for the entire range? Or do I have to format first and then use fstrim?

---

### Post by Cheesemill on 2012-09-25
No it doesn't.

Formatting only rewrites the filesystem table which is stored at the beginning of the drive, the rest of the drive remains untouched during a format.

---

### Post by Asmodai on 2012-09-25
Got it, thank you! When I think about it, there shouldn't be any disadvantage to simply running fstrim after formatting anyway.

---

