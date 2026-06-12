---
title: "Allocating unallocated space"
date: 2009-11-02
forum: General Help
---

### Post by rmcellig on 2009-11-02
I have some unallocated space I want to add to sda3. How exactly do I do this?

---

### Post by dcstar on 2009-11-02
> **rmcellig said:**
> I have some unallocated space I want to add to sda3. How exactly do I do this?

Boot off a Live CD, use the Partition Editor to move the first existing partition to the start of the disk, then you can expand the other partition into the free space.

You can search out detailed instructions on moving/expanding partition.

Of course, if have enough RAM you can simply delete the swap partition.

---

