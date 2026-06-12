---
title: "merge swap partition into ubuntu partition"
date: 2012-05-26
forum: General Help
---

### Post by Brizlitman on 2012-05-26
I formatted the swap partition and i want to merge this into my ubuntu partition. How do I do this?

---

### Post by wilee-nilee on 2012-05-26
> **Brizlitman said:**
> I formatted the swap partition and i want to merge this into my ubuntu partition. How do I do this?

Merge, do you mean have it mount with a boot?

---

### Post by Brizlitman on 2012-05-26
No. In windows 7 you can extended your C drive to  include an unallocated, empty partition. I want to know how to do that in ubuntu

---

### Post by wilee-nilee on 2012-05-26
> **Brizlitman said:**
> No. In windows 7 you can extended your C drive to  include an unallocated, empty partition. I want to know how to do that in ubuntu

Using gparted on a live cd/usb, linux can't do this on a live system.

Make sure on the live cd that no partitions are mounted, and if the partition that you want to extend is not held in an extended partition which needs to be extended first.

---

### Post by Mark Phelps on 2012-05-26
> **Brizlitman said:**
> No. In windows 7 you can extended your C drive to  include an unallocated, empty partition.

That's a contradiction of terms:
- Unallocated means the space is NOT assigned to a partition
- Empty (or otherwise) partition means the space IS assigned to a partition.

The same space on a drive can't be BOTH unallocated and partitioned.

---

### Post by wilee-nilee on 2012-05-26
[COLOR=White].[/COLOR]

---

