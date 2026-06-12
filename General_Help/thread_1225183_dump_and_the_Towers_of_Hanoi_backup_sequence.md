---
title: "dump and the Towers of Hanoi backup sequence"
date: 2009-07-28
forum: General Help
---

### Post by ianhaycox on 2009-07-28
Hi,

I'm using dump to backup /home on a daily basis with incremental dump. The dump manual page suggests a modified 'towers of hanoi' sequence for dump levels, e.g. 3, 2, 5, 4, 7, 6, 9, 8, 9, ... to reduce backup file sizes and restore time.

Trying to get my head around it I've come up with the following table. Am I on the right lines or have I missed something ?

```

Day of		Dump	Restore
month		level	level
1		0	0
2,9,16,23,30	3	0, 1*, 3
3,10,17,24,31	2	0, 1*, 2
4,11,18,25	5	0, 1*, 2, 5
5,12,19,26	4	0, 1*, 2, 4
6,13,20,27	7	0, 1*, 2, 4, 7
7,14,21,28	6	0, 1*, 2, 4, 6
8,15,22,29	1	0, 1

```

Level 1 is the weekly dump and the items marked * are only required from the second week.

There still seems to be occasions when quite a few dumps need to be restored. Is this table correct ?

Thanks.

---

