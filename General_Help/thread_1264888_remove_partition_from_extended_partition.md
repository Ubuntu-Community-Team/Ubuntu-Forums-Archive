---
title: "remove partition from extended partition?"
date: 2009-09-12
forum: General Help
---

### Post by daweefolk on 2009-09-12
I recently installed mythbuntu alongside my linux mint installation. I want to resize it because right now it's in an extended partion next to my swaps with only 300 MB left open. how can I remove the mythbuntu partition from the extended one and grow it with the 20GB i have open in an unallocated space?
or, would creating a copy of the partition and deleting the one in the extended partition work?

---

### Post by raymondh on 2009-09-12
> **daweefolk said:**
> I recently installed mythbuntu alongside my linux mint installation. I want to resize it because right now it's in an extended partion next to my swaps with only 300 MB left open. how can I remove the mythbuntu partition from the extended one and grow it with the 20GB i have open in an unallocated space?
or, would creating a copy of the partition and deleting the one in the extended partition work?

[http://gparted.sourceforge.net/larry/move/move.htm](http://gparted.sourceforge.net/larry/move/move.htm)
[http://www.howtoforge.com/partitioning_with_gparted](http://www.howtoforge.com/partitioning_with_gparted)

Good luck.  Back-up.

---

### Post by daweefolk on 2009-09-12
so asking a more specific question: if i copy the mythbuntu partition FROM the extended area TO the new partition from the unallocated space, will the grub file still work from the copy?

---

### Post by dcstar on 2009-09-12
> **daweefolk said:**
> so asking a more specific question: if i copy the mythbuntu partition FROM the extended area TO the new partition from the unallocated space, will the grub file still work from the copy?

If you delete/move partitions you should probably reinstall Grub as partition counts/ids may change and things will cease to boot up.

There are simple procedures to do this already in the forums.

---

