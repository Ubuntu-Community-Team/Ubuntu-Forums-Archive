---
title: "Extended Partition Editing"
date: 2010-05-23
forum: General Help
---

### Post by crazyamerican on 2010-05-23
I have Ubuntu installed on 60GB HD on a 30GB extended partition containing Ubuntu and a 2GB swap space. The remaining 30GB is used for backup.

I recently bought a 500GB external HD that I use to backup my computer and few other things. I want to get rid of the backup partition on my computer and extend the extended partition to cover the rest of it.

I booted with the LiveCD and started Gparted. When I try to do it with Gparted, it will allow me to delete the backup partition and extend the extended partition to cover the remaining space, but the existing logical partitions remain unchanged. It won't allow me to grow the logical partition containing Ubuntu to cover the remaining space inside the extended partition, even after I have moved the swap space to the other end to give it room. Is there a way to do this?

NOTE: I did not apply any of these operations, my computer has not been changed by Gparted.

---

### Post by Elfy on 2010-05-23
Possibly need to turn the swap off - right click swap partition and turn it off.

As I have no idea how the partitions are laid out I am taking a stab at them being

install  swap  unallocated

You'd need to move the swap to the end so install and unallocated are next to each other. Alternatively delete the swap - resize the install and create a new swap at the end.

---

### Post by Mark Phelps on 2010-05-23
Did you confirm that the logical partition is unmounted?  I would check that to be sure.

---

