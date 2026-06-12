---
title: "Move unallocated space to extended partition"
date: 2012-08-01
forum: General Help
---

### Post by gdawg on 2012-08-01
Hi,

How do I move unallocated scsi drive space to the extended partition. When I created the extended partition it included all of the unallocated space. Since then I've created several logical partitions and the extended partition has shrunk to the cumulative sizes of those partitions. I have approximately 300 GB that is unallocated that I want to add to the extended partition. Can anyone tell me how to do this? Using Gparted, when I select the extended partition there is no option to resize it.

---

### Post by ahallubuntu on 2012-08-01
The extended partition doesn't "shrink" when you create or delete logical partitions.  Once you make an extended partition, you can create/delete partitions inside of it at will.  If you delete a logical partition inside the extended partition, you could shrink the extended partition if desired to use the allocated space elsewhere (say in a primary partition).

If you have resized a primary partition to create new free space, you can grow the extended partition adjacent to it, then you can grow a logical partition or create a new one inside the extended.

Perhaps you could take a screenshot of Gparted showing your current partition scheme?

---

### Post by Shadius on 2012-08-01
> **ahallubuntu said:**
> The extended partition doesn't "shrink" when you create or delete logical partitions.  Once you make an extended partition, you can create/delete partitions inside of it at will.  If you delete a logical partition inside the extended partition, you could shrink the extended partition if desired to use the allocated space elsewhere (say in a primary partition).

If you have resized a primary partition to create new free space, you can grow the extended partition adjacent to it, then you can grow a logical partition or create a new one inside the extended.

Perhaps you could take a screenshot of Gparted showing your current partition scheme?

Yes, screenshot please!

---

### Post by gdawg on 2012-08-01
Thank you ahallubuntu and Shadius for your responses. Here is the screenshot:

---

### Post by plucky on 2012-08-01
You need to boot a Live CD or USB and then turn off SWAP which is mounted on the Live CD.This will unlock the extended partition.

Notice the keys to the left of the **File System column**.That means the file system is mounted and locked.

Once the swap file is unlocked and all the partitions in the extended partition are un-mounted,you will now be able to resize the extended partition and the un-allocated space will move into the extended partition.You will now be able to extend the existing partitions inside the extended partition or create new logical partitions.


Good Luck

---

### Post by gdawg on 2012-08-01
> **plucky said:**
> You need to boot a Live CD or USB and then turn off SWAP which is mounted on the Live CD.This will unlock the extended partition.

Notice the keys to the left of the **File System column**.That means the file system is mounted and locked.

Once the swap file is unlocked and all the partitions in the extended partition are un-mounted,you will now be able to resize the extended partition and the un-allocated space will move into the extended partition.You will now be able to extend the existing partitions inside the extended partition or create new logical partitions.


Good Luck
Thank you plucky. You are correct. I booted with Gparted live cd and was then able to move extended partition into unallocated space. Thanks alot.

Regards,

Glen

---

