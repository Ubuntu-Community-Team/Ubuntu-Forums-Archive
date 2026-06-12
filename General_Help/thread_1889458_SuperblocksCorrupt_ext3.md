---
title: "Superblocks/Corrupt ext3"
date: 2011-12-01
forum: General Help
---

### Post by Geekylad on 2011-12-01
Hi

I've tried everything in this article:

[I][http://www.cyberciti.biz/faq/recover...ted-partition/]("http://www.cyberciti.biz/faq/recover-bad-superblock-from-corrupted-partition/")
but to no avail. None of the backup superblocks worked.
[/I]
 
I still have a non-bootable system, any suggestions?

TIA

---

### Post by dandnsmith on 2011-12-01
What makes you thinks it's a bad superblock - after all there are a myriad of reasons why a system might be non-bootable!

---

### Post by Geekylad on 2011-12-01
> **dandnsmith said:**
> What makes you thinks it's a bad superblock - after all there are a myriad of reasons why a system might be non-bootable!

When booting the system I got:

> 
/dev/device contains a file system with errors, check forced.
/dev/device: Inodes that were part of a corrupted orphan linked list found

/dev/device : UNEXPECTED INCONSISTENCY; RUN fsck MANUALLY
    (i.e., without -a or -p options)
mountall: fsck / [1090] terminated with status 4
mountall: Filesystem has errors: /So I booted with a LiveCD.

Running fsck gave bad superblock errors

mke2fs -n /dev/device

Noted down the backup superblocks

fsck -b 32768 /dev/device (and all the other backup superblocks)

..and the contents of that article above and I still can't boot. Gparted LiveCD no use either.

---

### Post by dandnsmith on 2011-12-02
I don't know whether you should be concerned, but, in the article it recommends use of *dumpe2fs* where you have used *make2fs* - there is a possible difference between these of reporting presumed superblock locations instead of actual superblock locations.

As far as I can see, that is your only hope of recovering the filesystem.

---

