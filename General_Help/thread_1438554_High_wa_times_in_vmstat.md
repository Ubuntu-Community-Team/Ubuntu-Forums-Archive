---
title: "High wa times in vmstat"
date: 2010-03-25
forum: General Help
---

### Post by dragos2 on 2010-03-25
I noticed high wa times on one machine(3xhdd RAID5):

vmstat output under high write load (artificially created by me)

```

procs -----------memory---------- ---swap-- -----io---- -system-- ----cpu----
 0  6    116 121208 328872 905576    0    0     0  5461   79  226  0  0  0 100
..
0  8    116 149664 328836 876760    0    0     5  8321   69  197  1  0 18 81
..
 0  6    116 121208 328872 905576    0    0     0  5461   79  226  0  0  0 100
..
 0  4    116  64352 342052 917832    0    0     0  8359  173  696  0  1 37 62
..
 0  0    116 116396 329520 914676    0    0     0     5   42   49  0  0  100  0

```

The last line is a normal operation mode.

As you can see the wa times are very high when I write stress the disk.

Under sequantial or random read the system behaves very well.

The high wa is it because of RAID5 ?

---

