---
title: "Help verify my partitions are properly aligned, Windows, Linux dual boot."
date: 2012-06-20
forum: General Help
---

### Post by open.source on 2012-06-20
Hi, I have configured a dual boot on my OCZ Vertex 4 512 GB SSD and I would like  someone to help me verify proper partition alignment for optimal SSD endurance and performance. Here is my fdisk  -l output:

Disk /dev/sda: 512.1 GB, 512110190592 bytes
255 heads, 63 sectors/track, 62260 cylinders, total 1000215216 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x5334e02d

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048      206847      102400    7  HPFS/NTFS/exFAT
/dev/sda2          206848   500107263   249950208    7  HPFS/NTFS/exFAT
/dev/sda3       500107264   983310335   241601536   83  Linux
/dev/sda4       983310336  1000214527     8452096   82  Linux swap / Solaris

Can you also please tell me how you verified so I learn.

---

### Post by wilee-nilee on 2012-06-20
You don't have to run in 512 blocks.

---

### Post by Bucky Ball on 2012-06-20
Interesting. I also have this:

```
Disk /dev/sda: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
**Units = sectors of 1 * 512 = 512 bytes**
Sector size (logical/physical): 512 bytes / 512 bytes
```How do you change it from 512 blocks? During install? Formatting the disk? I'm presuming the latter. What difference does it make?

EDIT: Think I just answered my questions with some digging. ;)

---

### Post by open.source on 2012-06-20
What do you guys mean by not having to run with 512 blocks? I'm just asking if I am correctly aligned for optimal performance and endurance of my ocz SSD.

---

### Post by oldfred on 2012-06-20
Your starts just need to be divisible by 8.

Post on 8-sector boundaries alignment by srs5694
[http://ubuntuforums.org/showthread.php?t=1685666](http://ubuntuforums.org/showthread.php?t=1685666)
it's 8-sector (4096-byte) alignment - post 8
[http://ubuntuforums.org/showthread.php?t=1768635](http://ubuntuforums.org/showthread.php?t=1768635)
Alignment issues on 4K drives
[http://ubuntuforums.org/showthread.php?t=1635018](http://ubuntuforums.org/showthread.php?t=1635018)

---

### Post by open.source on 2012-06-20
So if my start sectors are divisible by 8 that means I am aligned, correct?

---

### Post by oldfred on 2012-06-20
That is what I understand from the threads linked.

---

