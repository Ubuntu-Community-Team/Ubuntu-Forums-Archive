---
title: "fatsort problems"
date: 2011-02-14
forum: General Help
---

### Post by 3602 on 2011-02-14
I have an audio recorder that doubles as a music player. It can play WAV files.
So I put in some WAV files and they are out of order, even if they are named numerically. Read somewhere about a little CLI software called *fatsort* so I installed that, hoping to solve my problems.
The device is located at */dev/sdc*. So naturally I write *fatsort /dev/sdc*, it says something about permission. So *sudo fatsort /dev/sdc*.
Thing is, it says:
```
sort_fs: Device or resource busy!

```
If I "eject" it (unmount) then it says something about cannot read boot sector or headers.
On Windows there is FAT Sorter. It does not work in WINE. So every time I put something in, I have to get to a Windows computer to sort it.
It seems like *fatsort* is the only program that sorts FAT systems in Ubuntu/Linux.
What to do?
Thank you very much.

---

### Post by 3602 on 2011-02-14
Great. Actually according to *fdisk -l* my drive to be sorted is */dev/sdc1* instead of just */sdc*. Solved.

---

