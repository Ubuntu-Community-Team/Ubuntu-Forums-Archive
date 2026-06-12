---
title: "I have partitioned my hard drive from ntfs to unallocated somehow."
date: 2009-08-29
forum: General Help
---

### Post by str8outtacpt on 2009-08-29
i do not understand why my window will not boot because i never commit any partitions to my hard drive and i have no way of backing it up. is there alternative way of getting my files off or is there a way to check to see if all of my files are still on my computer?

---

### Post by GSF1200S on 2009-08-29
> **str8outtacpt said:**
> i do not understand why my window will not boot because i never commit any partitions to my hard drive and i have no way of backing it up. is there alternative way of getting my files off or is there a way to check to see if all of my files are still on my computer?

It sounds like the ntfs partition is gone. Open a terminal and type:

```
sudo fdisk -l
```

And see if any of the printed partitions are ntfs. You can post the results in this thread so we can try to help you.

Now, I dont know how important your files are, but you can still get them back. It depends on what youre willing to spend or how much effort youre willing to go through. You see, when data is 'deleted,' its still on the HD, its just not indexed by the OS/filesystem. The raw data is still there, so it is recoverable. This is the reason for programs like Eraser and secure-delete, shred, etc. I suppose you could try a windows CD and see if the repair function will work, although most likely then you will need to boot ubuntu live cd and reinstall/configure grub.

Good luck and post the contents of above command :)

---

### Post by fluffman86 on 2009-08-29
If gparted is showing that you only have 1 unallocated partition, then you don't have any data available.  The drive has been formatted and it's essentially gone, depending on exactly *how* it was formatted or erased.

Some data recovery specialists may still be able to recover it, but I wouldn't get my hopes up: if they can, it may be partially missing or corrupted, and it will be VERY expensive.

---

