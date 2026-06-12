---
title: "Cannot Format Flash Drive after dd"
date: 2012-05-20
forum: General Help
---

### Post by Orcris on 2012-05-20
I just tried dd'ing an ISO to my flash drive, but someone closed the terminal while this was happening and stopped the dd. Now, when I opened the KDE Partition Manager and tried to format my drive, it gave me an error saying that I needed a new partition table. I created one, but when I tried adding a new partition, it gave me the same error. How do I fix this?

---

### Post by oldfred on 2012-05-21
Either rerun the dd to completion. It has written a partition table but only part of the partition, so it does not see the end.

I am not sure testdisk would fix it as dd is writing bit by bit and any interruption corrupts it.

You may be able to write all zeros and then be able to reformat, also, but not sure how that works with flash drives.

---

