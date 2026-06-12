---
title: "Unallocated space, how to resize /home partitions?"
date: 2012-05-28
forum: General Help
---

### Post by DaveDeviant on 2012-05-28
I remvoed my windows OS and now I want to resize my /home partition with that unallocated space. The main problem is that the free space is not under my sda4. How to move it there and than resize my /home partition?

[http://img844.imageshack.us/img844/3831/screenshotfrom201205290.png](http://img844.imageshack.us/img844/3831/screenshotfrom201205290.png)

---

### Post by wilee-nilee on 2012-05-28
You will have to move the sda3 to the left it will move as a whole partition it will take awhile.

You will then expand the sda4 into the unallocated that is left, then move the sda5, and sda7 as you like as far as which one is which, I assume the sda7 is the home.

I would if me move the sda5 to the left to where the extended starts, and then decide to do the same with the swap and expand the sda7 to the left.

You really only have to expand the extended and the sda7, the rest can be moved as whole partitions.

You just right click each partition and then resize/move.

This is going to take a long time, I would estimate about 3 hours.

---

