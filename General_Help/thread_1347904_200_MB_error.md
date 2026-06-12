---
title: "200 MB error"
date: 2009-12-06
forum: General Help
---

### Post by abx_dx on 2009-12-06
Hi everyybody, this is my new post, also I'm a Linux newbie. I use 9.10 Karmic Koala. I have a interesting problem.

I have .iso file which is about 700 MB, I want to copy this file to another partition (source partition=ext4, destination partition=ntfs), but when I was copying the file, operation stopped at 200.1 MB and gave this error: "error while reading input file: Input/output error"

After that, I decided to split the file into pieces which were smaller than 200 MB with lxsplit in terminal. First I selected 100 MB for pieces but when it was generating third file, it gave same error: "error while reading input file: Input/output error". Later I selected 50 MB for pieces but when it was generating 5th file, it gave same error.

I have 1 GB memory and 1 GB swap file. While I was operating this process i gave "free" command to see the memory status:

```

             total       used       free     shared    buffers     cached
Mem:       1024732     986436      38296          0      10912     719120
-/+ buffers/cache:     256404     768328
Swap:      1004020          0    1004020

```
what is the wrong?

---

### Post by dcstar on 2009-12-06
> **abx_dx said:**
> Hi everyybody, this is my new post, also I'm a Linux newbie. I use 9.10 Karmic Koala. I have a interesting problem.

I have .iso file which is about 700 MB, I want to copy this file to another partition (source partition=ext4, destination partition=ntfs), but when I was copying the file, operation stopped at 200.1 MB and gave this error: "error while reading input file: Input/output error"

After that, I decided to split the file into pieces which were smaller than 200 MB with lxsplit in terminal. First I selected 100 MB for pieces but when it was generating third file, it gave same error: "error while reading input file: Input/output error". Later I selected 50 MB for pieces but when it was generating 5th file, it gave same error.
.........
what is the wrong?

You have a disk error just over 200MB into the file, or you do not have enough disk space.

---

### Post by abx_dx on 2009-12-07
> **dcstar said:**
> You have a disk error just over 200MB into the file, or you do not have enough disk space.

My disk space is extremely enough but you're right because the cd which source of .iso file was in bad condition. I wanted to rescue it but i failed.

This was a very interesting experience for me. Thank you. The problem is solved ;)

---

