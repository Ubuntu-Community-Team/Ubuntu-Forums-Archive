---
title: "250 GB external hard drive only holds 239 MB"
date: 2011-03-15
forum: General Help
---

### Post by jhsu802701 on 2011-03-15
I have a 250 GB Seagate Expansion Portable Drive that can't hold more than 239 MB.  I'm trying to copy an 804 MB file, but I get a "no space left on device" error message after only 239 MB of it has been copied.  In other words, the drive's capacity has mysteriously shrunk by over 99.9%.

This happens in NTFS (the drive's original format) and in ext2 and ext3.

What's going on here?

---

### Post by gyyug78fg87ogguiioioioioi on 2011-03-16
i dont know, but if u dont have nothing important on it meaybe you should try to format it

---

### Post by Hedgehog1 on 2011-03-16
Take a look at the partition layout on the drive (using Disk Utility or gparted).

I think you have a small partition that is formatted, and the rest of the drive is unallocated.

***The Hedge***

:KS

---

