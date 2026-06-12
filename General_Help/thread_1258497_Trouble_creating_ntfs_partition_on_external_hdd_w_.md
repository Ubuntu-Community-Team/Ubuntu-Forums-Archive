---
title: "Trouble creating ntfs partition on external hdd w/ gparted"
date: 2009-09-05
forum: General Help
---

### Post by jsheppard on 2009-09-05
Hey all,

Wondering if anyone might have a solution to this problem. I want to reformat my 320gb external hard drive to just have a single primary ntfs partition. Using gparted, I've deleted all partitions so it's all just plain unallocated space. 

However when I select "create new [primary] partition," I have the options of using the following filesystems:
ext2,ext3,ext4,fat16,fat32,linux-swap,reiserfs,unformatted

But the following filesystems are greyed out in the menu (not choosable): hfs,hfs+,jfs,ntfs,reiser4,ufs,xfs

Not sure if it matters, but I have the latest "ntfs-3g" package installed, and I'm running Ubuntu Jaunty 64-bit.

I could try gparted liveCD if that's the logical next step, though it seemed that this shouldn't be necessary since this is simply an external (and now totally unallocated) hdd.

Thanks much

---

### Post by Efwis on 2009-09-05
I presume your planing on putting windows on the external hdd? If that is the case then let windows do the partitioning on it. otherwise you may want to try the live cd and see if that option is grayed out.

---

### Post by P4man on 2009-09-05
sounds like you dont have ntfsprogs installed for some reason? Try:

```
sudo apt-get install ntfsprogs
```

---

### Post by jsheppard on 2009-09-05
Thanks you guys,

To efwis, I actually just want this as external/mobile storage. I'd be happy to use ext3 except that it isn't readily supported (as far as I am aware) on Windows and OS X, unless you install drivers which isn't feasible on e.g. university computers.

To P4man, you are correct! It probably didn't come installed standard because (I believe) ntfs is not open source.

Marking this thread as solved.

Cheers,

John

---

### Post by P4man on 2009-09-05
the ntfs driver and ntfsprogs ARE opensource, and they do come preinstalled. afaik. The driver for sure, perhaps not the ntfs progs (needed for formatting, not just reading or writing)

---

