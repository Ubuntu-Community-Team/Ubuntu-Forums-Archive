---
title: "Share swap between Ubuntu and Windows XP?"
date: 2011-01-21
forum: General Help
---

### Post by imwithid on 2011-01-21
I've been trying to find a fix to this problem. It seems inefficient to have to allocate two partitions for swap / pagefile when one can suffice (especially when allocating at least two to four gigabytes of space to each)

This is especially important when performance is to be maximized. I realize that this is, perhaps, bordering on pedantic, but if one can place a partition at the beginning (outer diameter) of the hard drive, for swap, one can then optimize performance for the page file and temporary files writing to disk ( and in addition, not interfering with the other files on the Windows partition.

The best method (given that Ubuntu cannot read FAT32 or NTFS partitions for swap) seems to be to install a driver within Windows that can detect Unix based file systems (EXTx).

Does anyone have any suggestions? (I may have to edit this post to clarify ... long night).

---

### Post by kidders on 2011-01-22
Hi there,

Afaik Windows doesn't support virtual memory filesystems, so in order for Linux & Windows to use the same partition, your Ubuntu would have to use swap files too, which could be quite a bit slower.

To be honest, assuming you're a fairly typical computer user, there's very little point in going over the top in an effort to increase virtual memory performance. Paging is just plain slow ... Even if you managed to *double* the throughput of your virtual memory, the difference it would make would most likely be imperceptible. In practical terms, once your system starts paging, does it really matter how many hundreds of times slower memory access becomes?

Incidentally, if you really do want to try it, there's no reason you can't put your Ubuntu's swap file on a FAT32 filesystem.

Leaving virtual memory performance per se aside, one factor that might more perceptibly affect real-life performance is what your system can do *while* it's paging. Are your Windows/Linux virtual memory spaces on the same physical disks as their system partitions?

> **imwithid said:**
> It seems inefficient to have to allocate two partitions for swap / pagefile when one can sufficeThat depends on what you mean by "efficient". Generally speaking, efficiency and performance have an inverse relationship, in that you often have to choose one or the other.

I hope that helps.

---

### Post by sammiev on 2011-01-22
Hi kidders and many thanks for the great read. Your words were very well chosen! Thanks :)

---

### Post by dcstar on 2011-01-22
> **kidders said:**
> 
........
Incidentally, if you really do want to try it, there's no reason you can't put your Ubuntu's swap file on a FAT32 filesystem.
........

Apart from the fact that every Linux System File/Folder **must** be on a Linux filesystem?

---

### Post by kidders on 2011-01-22
> **dcstar said:**
> Apart from the fact that every Linux System File/Folder **must** be on a Linux filesystem?

That's simply not true. Linux files (whether system-related or not) can be stored on virtually any filesystem. Out of interest, what makes something a *Linux* filesystem?

---

