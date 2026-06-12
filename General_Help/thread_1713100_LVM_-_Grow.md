---
title: "LVM - Grow?"
date: 2011-03-23
forum: General Help
---

### Post by JaizEdelmann on 2011-03-23
Hey guys i have a question about LVM, im currently planning on setting up LVM with 4x HDD's however when i want to grow my LVM directory can i just add a new HDD and make grow on the existing LVM virtual drive without losing any data on the current disks in the LVM virtual drive?

---

### Post by JaizEdelmann on 2011-03-23
/Bump

---

### Post by falko on 2011-03-23
Yes, this is possible. This should answer all your LVM questions: [http://www.howtoforge.com/linux_lvm](http://www.howtoforge.com/linux_lvm) :)

---

### Post by deconstrained on 2011-03-23
Sounds like what you really want is Linux software RAID. LVM is mainly for setting up multiple partitions on a disk surface that are easier to manage (and more flexible) than partitions created through directly modifying the partition table. You can have a virtually unlimited number of LVM volumes, resize easily, make filesystem snapshots easily and a host of other great things with LVM, but I don't think you can tell LVM to create/modify a logical volume or volume group in such a way that it uses multiple devices. That's where mdadm comes in.

---

### Post by JaizEdelmann on 2011-03-23
> **deconstrained said:**
> Sounds like what you really want is Linux software RAID. LVM is mainly for setting up multiple partitions on a disk surface that are easier to manage (and more flexible) than partitions created through directly modifying the partition table. You can have a virtually unlimited number of LVM volumes, resize easily, make filesystem snapshots easily and a host of other great things with LVM, but I don't think you can tell LVM to create/modify a logical volume or volume group in such a way that it uses multiple devices. That's where mdadm comes in.

I actually dont want a RAID because i dont want if 1 hdd breaks to lose everything and i dont want to run RAID5 and lose 1 HDD outa 3 regarding space :)

---

### Post by deconstrained on 2011-03-23
So then...You just want to add hard drives and use them for extra storage space? That's a trivial matter that doesn't require LVM.

---

### Post by jerome1232 on 2011-03-23
> **JaizEdelmann said:**
> Hey guys i have a question about LVM, im currently planning on setting up LVM with 4x HDD's however when i want to grow my LVM directory can i just add a new HDD and make grow on the existing LVM virtual drive without losing any data on the current disks in the LVM virtual drive?

Sounds like you want to use LVM to span a single volume over multiple disks? Yes you can do that with LVM, it is however not fault tolerant, meaning if you lose one disk you can lose all of your data.

---

### Post by JaizEdelmann on 2011-03-23
> **jerome1232 said:**
> Sounds like you want to use LVM to span a single volume over multiple disks? Yes you can do that with LVM, it is however not fault tolerant, meaning if you lose one disk you can lose all of your data.


Wouldent you just lose the data on the drive that breaks down? Thats why i though i could run with LVM instead of a raid where you will lose all data if one disk breaksdown unless u run RAID5 or similiar

> **deconstrained said:**
> So then...You just want to add hard drives and use them for extra storage space? That's a trivial matter that doesn't require LVM.

Yes but i want all my hdd's and future hdd's to be combined into a big black hole / virtual folder or virtual drive of some sorts

---

### Post by deconstrained on 2011-03-23
> **JaizEdelmann said:**
> Wouldent you just lose the data on the drive that breaks down? Thats why i though i could run with LVM instead of a raid where you will lose all data if one disk breaksdown unless u run RAID5 or similiar
You would lose the data because you'd then have an incomplete/corrupt filesystem. Think of it: if **half** the blocks on your hard drive went bad, you'd have quite a bit of a problem, for which you'd need some kind of professional-grade data recovery software to get the contents back (or at least what wasn't on the side that went bad).

> **JaizEdelmann said:**
> Yes but i want all my hdd's and future hdd's to be combined into a big black hole / virtual folder or virtual drive of some sorts
You can always grow a RAID 5. The storage space to drives ratio (and performance) would improve, and you'd be less likely to lose all your data (nonzero fault tolerance).

If you want easy combination of drives into storage space, get a drobo. They do it all for you - just put a drive in and it automatically grows/self-heals.

---

### Post by JaizEdelmann on 2011-03-24
> **deconstrained said:**
> You would lose the data because you'd then have an incomplete/corrupt filesystem. Think of it: if **half** the blocks on your hard drive went bad, you'd have quite a bit of a problem, for which you'd need some kind of professional-grade data recovery software to get the contents back (or at least what wasn't on the side that went bad).


You can always grow a RAID 5. The storage space to drives ratio (and performance) would improve, and you'd be less likely to lose all your data (nonzero fault tolerance).

If you want easy combination of drives into storage space, get a drobo. They do it all for you - just put a drive in and it automatically grows/self-heals.


I though LVM didnt split on block level but on file level? so that 1 file would only exsist on 1 drive out the drives or partitions in the virtual folder?

in RAID5 if you have 3 harddrives, 1 drive would be used to disc management correct ? and if i have 4 still 1 drive would be used? or would i have to increase my disc numbers to 6 and then 2 dries would be used as disc management?

---

### Post by deconstrained on 2011-03-24
> **JaizEdelmann said:**
> I though LVM didnt split on block level but on file level? so that 1 file would only exsist on 1 drive out the drives or partitions in the virtual folder?

in RAID5 if you have 3 harddrives, 1 drive would be used to disc management correct ? and if i have 4 still 1 drive would be used? or would i have to increase my disc numbers to 6 and then 2 dries would be used as disc management?
Regardless of how it's split, the filesystem would be borked. You can't just slice away half the physical medium on which a filesystem rests and still have it working properly for the half that remains.

RAID 5 actually distributes redundancy (in the form of parity bytes) across the array, to even the wear and use. I believe RAID 3 is the level that uses a dedicated drive for storing parity.

---

### Post by JaizEdelmann on 2011-03-25
> **deconstrained said:**
> Regardless of how it's split, the filesystem would be borked. You can't just slice away half the physical medium on which a filesystem rests and still have it working properly for the half that remains.

RAID 5 actually distributes redundancy (in the form of parity bytes) across the array, to even the wear and use. I believe RAID 3 is the level that uses a dedicated drive for storing parity.

Thank for all your help deconstrained ill use the MDADM and create a RAID5 setup for myself seems like thats the way i need togo :)

All my last pieces of hardware arrived today so i can start up the process later on :)

---

