---
title: "Input/Output error all of a sudden"
date: 2011-08-04
forum: General Help
---

### Post by Neraste on 2011-08-04
Hello everyone!

I'm using Ubuntu Studio 11 on my laptop I share with Windows 7 and for several days I have worked on a project in a NTFS disk. Yesterday evening, I was completing my work but today, I can't open it neither on Ubuntu, nor on Windows!

On Win, I'm told the files are corrupted/the folders don't exist and on Linux, a **ls** command tells me: **input/output error**.

What is really weird is that the files written with Windows are still available, but not the ones written with Ubuntu! And of course this problem occurs only in *this* project directory.

Well, I have tried few things :

**ntfsfix** doesn't see anything unusual.
The **SMART** state of my drive is OK (my laptop is one month old, so...)
**gparted** tells me:
```
ntfsresize v2.0.0 (libntfs 10:0:0)
Device name : dev/sda7
NTFS volume version : 3.1
Cluster size : 4096 bytes
Current volume size : 361574167040 bytes (361575 MB)
Current device size : 361574170624 bytes (361575 MB)
Checking filesystem consistency...
Accounting cluster...
Cluster accounting failed at 328623 (0x503af): missing cluster in $Bitmap
Cluster accounting failed at 791280 (0xc12f0): extra cluster in $Bitmap

...

Filesystem check failed! Totally 65656 cluster accounting mistmatches.
ERROR: NTFS is inconsistent. Run chkdsk /f on Windows then reboot it TWICE!
[not enough place on my screen to read the next...]

```Well, I really don't know what happened. I think that **chkdsk **will fix the errors, but **will it remove any file or make any file unreadable?** That is something to avoid because I *can't* loose those files! I prefer waiting and be sure to apply the good solution.

I'm turning in panic mode since all my project is in jeopardy! I really don't understand why *only this* directory has that problem all of a sudden.

So, if you have any suggestion... I really need your help/advises!

---

