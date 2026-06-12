---
title: "Resize EXT3"
date: 2009-12-29
forum: General Help
---

### Post by ndmp on 2009-12-29
Hey, does anyone know how I can resize my ext3 partition? I tried running a Kanotix Live CD and doing it from that, but the only partition application I could find on it was QTParted which doesn't support resizing ext3 drives (I'm not sure why this is the case, as it makes the application effectively useless).

Can anyone recommend a live CD distro with a partition manager that can resize ext3 partitions? Could I use the Ubuntu boot disk? (I don't think it has a partition manager)

Thanks.

---

### Post by Cheesemill on 2009-12-29
You can use Gparted on the Ubuntu Live CD.

---

### Post by mutex023 on 2009-12-29
The ubuntu live cd has a partition manager, System > Administration >Partition Editor. 
But I dont know whether it resizes ext3, give it a try and see.

---

### Post by ndmp on 2009-12-29
Thanks, will I need to set a root password?

---

### Post by Pipps on 2009-12-29
In LiveCD mode, there is no requirement to enter or set a password in order to use Gparted.

Gparted should happily resize an ext3 partition.

Let us know how it goes for you!

---

