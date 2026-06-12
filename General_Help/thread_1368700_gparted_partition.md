---
title: "gparted partition"
date: 2009-12-31
forum: General Help
---

### Post by chrissy.millichamp on 2009-12-31
How I do use or make a partition in gparted?
My second question is, how do I dual install  windows vista home premium beside Ubuntu 9.10 installed first?
thanks in advance :)

---

### Post by dcstar on 2009-12-31
> **chrissy.millichamp said:**
> How I do use or make a partition in gparted?
My second question is, how do I dual install  windows vista home premium beside Ubuntu 9.10 installed first?
thanks in advance :)

There are detailed instructions for both already in the forums, search them out.

Also installing Windows will overwrite the Ubuntu Grub boot loader, but the instructions have fixes for that.

---

### Post by Mark Phelps on 2009-12-31
> **chrissy.millichamp said:**
> How I do use or make a partition in gparted?
My second question is, how do I dual install  windows vista home premium beside Ubuntu 9.10 installed first?
thanks in advance :)

Just make sure that you do NOT use Gparted or the Ubuntu installer to shrink the Vista OS partition to make room for Ubuntu.  Be sure to use the Vista Disk Management utility to do that.

Once you have shrunk the Vista partition, you can use GParted to create the Ubuntu partition in the free space.

---

