---
title: "problem with harddisk?!"
date: 2011-01-23
forum: General Help
---

### Post by utkarshjadhav on 2011-01-23
I used ubuntu live CD (lucid lynx)
And formatted the whole harddisk.
My hard disk is 320 GB.
after formatting I tried installing windows 7 . But it shows only 280 GB .
but  ubuntu live cd disk manager shows me ... 320GB free space...
WHat to do?

---

### Post by srs5694 on 2011-01-23
That's probably mostly a units issue. Disk manufacturers use "GB" to mean 10^9 bytes, whereas until recently most others used "GB" to mean 2^30 bytes (a value that's now defined as gibibytes, or GiB). Thus, 320 GB = 320 * 10^9 / 2^30 = 289 GiB. The remaining 9 GiB discrepancy might be accounted for by one or two hidden partitions on the disk, a journal taking up space on the partition, etc.

---

### Post by utkarshjadhav on 2011-01-30
that helps.
I formatted the disk again.with boot installer.
its now showing 320 GB = 320 * 10^9 / 2^30 = 298 GiB.
thanks!

---

