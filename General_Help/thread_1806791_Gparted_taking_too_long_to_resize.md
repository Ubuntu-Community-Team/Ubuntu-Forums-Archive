---
title: "Gparted taking too long to resize"
date: 2011-07-18
forum: General Help
---

### Post by aconstantin on 2011-07-18
Hi everyone,

I know it's been a long time since the last post, but I want to share my experience, since, through some bad decisions, I believe I now have an upper bound for FS size and waiting time:

CPU: Intel(R) Core(TM)2 Duo CPU E8400 @ 3.00GHz
Mem/Swap: 2/1 GiB
HDD: Western Digital MyBook Studio Edition II 2TB
Connection: eSATA
Ubuntu: 10.04

Task: Shrink partition from 1.82 TiB to 901.70 GiB
Free space on partition, after resize: 38.42 GiB

13012769 regular files
409103 directories

Shrink time: 96:45:17

This was .. educational.

---

### Post by HiImTye on 2011-07-18
> **aconstantin said:**
> Hi everyone,

I know it's been a long time since the last post, but I want to share my experience, since, through some bad decisions, I believe I now have an upper bound for FS size and waiting time:

CPU: Intel(R) Core(TM)2 Duo CPU E8400 @ 3.00GHz
Mem/Swap: 2/1 GiB
HDD: Western Digital MyBook Studio Edition II 2TB
Connection: eSATA
Ubuntu: 10.04

Task: Shrink partition from 1.82 TiB to 901.70 GiB
Free space on partition, after resize: 38.42 GiB

13012769 regular files
409103 directories

Shrink time: 96:45:17

This was .. educational.
sometimes it's better just to copy what you need and start over lol

---

### Post by Mark Phelps on 2011-07-18
> **aconstantin said:**
> This was .. educational.

You beat my previous record!!

But, did you notice that GParted does the shrinkage twice -- once as a test, and second time, for real. So, unless there is a way to prevent the "test" pass, it's going to take TWICE as long as other tools.

---

### Post by oldfred on 2011-07-18
No matter what format you have if you only have 38GB free out of 1.82TB you do not have enough free space.

NTFS just about stops working with 10% free and Linux formats also need room, they usually hide 5% to prevent you from crashing when you get too little free space. And you have 1.82TB of data in one partition? How are you backing up. Before any major restructure you need good backups.

---

