---
title: "Using Clonezilla with an existing drive?"
date: 2009-10-05
forum: General Help
---

### Post by foogoo on 2009-10-05
I have a 1TB external HD I want to use with Clonezilla to backup my 250gb computer. Since I'll only be using 250gb or so of that external, is it possible to use the remaining space as I wish? Or will Clonezilla repartition the external every time I update the image?

I tried searching online and the Clonezilla site but couldn't see to find an answer. Thanks.

---

### Post by rbc on 2009-10-05
It depends on what you are trying to accomplish. If you want to “clone” the 250GB drive, then yes, you will lose any other data on the drive, because Clonezilla will overwrite the partition table. If you want to “image” the main Ubuntu partition, then no. In the latter case, Clonezilla will just write the image file(s) to whichever partition (on the terabyte drive) you tell it to, without touching any other partitions

---

### Post by foogoo on 2009-10-05
> **rbc said:**
> It depends on what you are trying to accomplish. If you want to “clone” the 250GB drive, then yes, you will lose any other data on the drive, because Clonezilla will overwrite the partition table. If you want to “image” the main Ubuntu partition, then no. In the latter case, Clonezilla will just write the image file(s) to whichever partition (on the terabyte drive) you tell it to, without touching any other partitions

Thanks for the reply. I guess all I really need is an image, I'll have to do that next time instead of cloning.

---

