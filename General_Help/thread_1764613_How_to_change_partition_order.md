---
title: "How to change partition order?"
date: 2011-05-21
forum: General Help
---

### Post by Julita on 2011-05-21
Hello everyone! I have several partitions, sda1 is win, sda6 is buntu; the question is how to switch them (sda1 - buntu; sda6 - win) The partitions operate in a descending order (the one that is in front is faster than the others, not to mention buntu is No.6 now)

---

### Post by oldfred on 2011-05-21
You cannot change a logical partition in the extended with the primary partitions.

You speed increase due to location on the drive is so small as you will not notice. You will not type faster. Your Internet is not faster and those are the main things you normally do with a desktop. If compiling a lot of programs then an SSD may make sense and that will be noticeable.

You can also get minor benefit from having a small system partition and your data in /home or data partitions. Then the heads do not have to move as far to find system files.

---

### Post by Stephen Morgan on 2011-05-22
Also, you can't put Windows on sda6, which will be an extended partition, because Windows can only booth from a Primary partition. Or at least, it could last time I used it, I don't expect Win7 to be any different.

---

### Post by Julita on 2011-05-22
For me it's not critical, since I use Win for data storage. I.e., can't format the partition; no space left.

> **Stephen Morgan said:**
> Windows can only booth from a Primary partition.

---

