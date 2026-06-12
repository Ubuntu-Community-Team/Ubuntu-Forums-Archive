---
title: "Partitions corrupted?"
date: 2009-07-15
forum: General Help
---

### Post by Superd00per on 2009-07-15
So yeah, heres the quick story.
I tried getting into windows by adding it to GRUB, didn't work so i decided to run windows recovery console and hit in FIXMBR and FIXBOOT so i could boot into it and backup all my data to a skydrive.
Obviously this wasn't the smartest thing to do, because it appears that all my partitions are corrupted as of that action.

Watch this:
```
root@ubuntu:/media# mount /dev/sda1 /media/sda1
root@ubuntu:/media# cd /media/sda1
root@ubuntu:/media/sda1# ls
???.??  ??8???8?.??8  ??y.??y
root@ubuntu:/media/sda1# fdisk -l

Disk /dev/sda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       11669    93731211   83  Linux
/dev/sda2   *       11670       14219    20482875    7  HPFS/NTFS
/dev/sda3           14220       14593     3004155    5  Extended
/dev/sda5           14220       14593     3004123+  82  Linux swap / Solaris
root@ubuntu:/media/sda1# 

```

Please share your thoughts on how to fix this.

---

### Post by manualqr on 2009-07-15
I don't think you're filesystems are beyond hope.. It's still recognized as ext3..

could you try using any graphical file browser to look at /media/sda1?

---

### Post by Superd00per on 2009-07-15
Every graphical file manager shows the same files as the directory listing with the same strange names.
Should I provide a screenshot?

---

### Post by philcamlin on 2009-07-15
yeah they dont look dead but i dont know about recovery 

its good that it still recognises them though as ext3 etc...

---

### Post by Superd00per on 2009-07-15
I'm starting to lose hope a little bit now, going to attempt a diffrent approach and i'll post the results

---

### Post by Superd00per on 2009-07-15
So yeah, i figured it out.
As you can see in my first post i was mounting without telling mount that it was a ext3 filesystem, therefor the strange character names and everything.
```

mount -t ext3 /dev/sda1 /media/sda1

```This did the trick, had to figure it out once.

Thanks for the suggestions posted. Case closed.

Edit: Sorry for the double post

---

