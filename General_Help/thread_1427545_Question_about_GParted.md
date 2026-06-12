---
title: "Question about GParted"
date: 2010-03-11
forum: General Help
---

### Post by blueshiftoverwatch on 2010-03-11
What would happen if the power went out when I was using a live CD with GParted to move partitions around? Or if I clicked "cancel" in the middle of the process?

Would chaos ensue? Or would my partitions just be non-sequitur which would cause lower efficiency because the data on the partition that was being moved when the process was stopped would be in two physical locations on the HD platters at once?

---

### Post by akand074 on 2010-03-11
If I'm not mistaken, it would only make those partitions unusable. You could just delete them and make them unallocated space and then just reformat them. Though I wouldn't take my word for it.

---

### Post by audiomick on 2010-03-11
I think it depends a bit on exactly where gparted was up to, but I am sure that neither of the two possibilities is something that you want to happen. Gparted needs to know where it is up to in order to successfully complete operations, and if you bail out or lose power, it doesn't any more, as far as I know. That is one of the reasons for doing backups before you start any partitioning operations.

---

### Post by Dayofswords on 2010-03-11
[http://ubuntuforums.org/showthread.php?t=1366754](http://ubuntuforums.org/showthread.php?t=1366754)
> Unfortunately during the "read-only" test (which is made after the selection of the optimal block size) my (idiot) little sister pushed "cancel"...

---

### Post by audiomick on 2010-03-11
@Dayofswords
yes, I remember that thread. The poor guy really had problems...

---

### Post by sgosnell on 2010-03-11
The partitions you were making would probably be borked, but you should be able to start over and remake the partitions.

---

