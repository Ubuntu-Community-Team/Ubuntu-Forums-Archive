---
title: "Add to partition?"
date: 2010-01-30
forum: General Help
---

### Post by Scooter_X on 2010-01-30
Once I have partitions all set up the way I want them, how hard is it then to take space from one and add it to another? Is that possible?

---

### Post by Miljet on 2010-01-30
Yes, that is possible.

1. If you have data on the partitions, back up before starting. The risk for data loss is small, but it could happen.

2. All partitions that are being changed need to by unmounted so it is best to use a live CD or a bootable GParted disk.

3. You cannot just randomly take space from one partition and add it to any other partition. If you want to shrink sda1 and add the space to sda2, that is pretty simple. Just shrink the sda1 partition first, then add the free space to sda2. If you want to shrink sda1 and add the space to sda3, you would have to shrink sda1, add the free space to sda2, then shrink sda2, and add that space to sda3, and so on. You cannot add space from a primary partition to a logical partition without changing the extended partition first. In other words, know exactly what you are doing before beginning.

4. It is going to take a long time because a lot of data has to be moved.

5. Understand what you are doing and BACKUP your data before beginning.

---

### Post by Scooter_X on 2010-01-31
Sweet. Thanks. I guess I'll make SURE I know what's up before I begin.

---

### Post by Scooter_X on 2010-02-01
Holy cow you were right about it taking forever... like 4 hours. And the worst part? Instead of moving 5gb like I wanted, I moved 500mb. It was still early and I was having trouble using my brain. :P Oh well, I now know how to do that. Thanks again.

---

### Post by Miljet on 2010-02-01
Glad it worked for you. Every time you try something new, you learn a little more. Keep it up. Just research what you want to do beforehand instead of charging ahead blindly.

---

