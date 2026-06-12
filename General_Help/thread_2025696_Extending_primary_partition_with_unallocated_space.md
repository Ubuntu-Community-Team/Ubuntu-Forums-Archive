---
title: "Extending primary partition with unallocated space"
date: 2012-07-14
forum: General Help
---

### Post by persianprez on 2012-07-14
Here's how it looks:
[http://i.imgur.com/PoXpM.png](http://i.imgur.com/PoXpM.png)

I'm trying to extend the sda2 using the unallocated space.  However, I have no idea how to.

Thanks in advance.

---

### Post by Vaphell on 2012-07-14
you should have an option in Partition menu (Move/Resize)

---

### Post by persianprez on 2012-07-14
> **Vaphell said:**
> you should have an option in Partition menu (Move/Resize)

Yes, but it doesn't let me make it larger.

---

### Post by plucky on 2012-07-14
> **persianprez said:**
> Yes, but it doesn't let me make it larger.

Use the windows disk tools to extend the sda2 partition.

You have to move the unallocated space to be adjacent to the partition you want to extend.

Is this anything to do with Ubuntu?

Seems to be all windows partitions.

Good luck

---

### Post by persianprez on 2012-07-14
> **plucky said:**
> Use the windows disk tools to extend the sda2 partition.

You have to move the unallocated space to be adjacent to the partition you want to extend.

Is this anything to do with Ubuntu?

Seems to be all windows partitions.

Good luck

I'm not able to boot into Windows.  I need to run my recovery partition but it needs my primary (sda2) to be the full size it came with.  I'm running my live cd just for gparted in Ubuntu.

I need to move the unallocated space under the extended section so I can extend my primary (sda2).

---

### Post by plucky on 2012-07-15
You have to do this in order.

1) Right click on /dev/sda3 and increase the size of the partition to encompass the un-allocated space.**Then Apply.**

2) Select /dev/sda5 and resize/move the partition to the right.**Then apply.** This step might take a long time if there is a lot of data to move.

3) Select /dev/sda3 and reduce the size if the partition to the same as /dev/sda5.

4)The un-allocated space will now be directly behind the /dev/sda2 partition,which you should now be able to extend the partition.

Good luck

---

