---
title: "extending ubuntu partition (help)"
date: 2011-08-03
forum: General Help
---

### Post by ericsoderstrom on 2011-08-03
I am dual-booting 11.04 alongside windows 7. I shrunk my w7 partition, and would like to extend my ubuntu partition to fill up the remaining space. When I boot from GParted live cd, and attempt to 'move/resize' my ubuntu partition, it simply fails. =(
Any idea what's going on?

It doesn't really give an error message either, simply 'failed to move/resize [partition name]'

---

### Post by Blasphemist on 2011-08-03
What it took me a bit to see when I did this was that the extended partition must be expanded into the newly available space before the logical partition within the extended partition could be.

There is some risk in moving a partition. Be sure to backup. Or, create a new logical partition or more than one in the new space.

---

### Post by ericsoderstrom on 2011-08-03
I tried once again to expand the extended partition, this time changing it to 'align to none' rather than 'align to MiB'. It worked, and I was subsequently able to expand the logical partition. However, I wasn't able to expand the logical partition to completely fill up the extended partition. Now there is this little bit of unallocated space in the extended partition, that I'm evidently unable to expand into. =(
It's kind of annoying, but not extremely problematic.

---

### Post by krytorii on 2011-08-03
I had similar problems. If you have a swap partition, right click it and select "swapoff". Extend the extended partition, then the ubuntu partition. Depending on where your partitions are, you may need to move them around so the empty space is next to the extended and then ubuntu partition

---

### Post by Blasphemist on 2011-08-03
It's common for a few MB to get left unused between partitions and shouldn't be worried about.

---

