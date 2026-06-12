---
title: "Create A new primary partition"
date: 2010-02-25
forum: General Help
---

### Post by MelDJ on 2010-02-25
i have 2 partitions. one with vista and the other with ubuntu. i would like to make another primary partition from the free space in my ubuntu partition. 
anyway to do this?

---

### Post by mike555 on 2010-02-25
install " gparted " or use a live CD (using live CD might be best )  - be carefull -

---

### Post by MelDJ on 2010-02-25
i have used gparted and resized the partition to 42gbs. 
but it only comes up as a partition under sda2. i want it to be: sda1= vista sda2= ubuntu sda3= empty

see the screenshot too.

---

### Post by uncle-c on 2010-02-25
You can label ext2/2/4 partitions with e2label and NTFS ones with ntfsprogs.  Make sure the partitions are unmounted before you alter them.

---

### Post by lotharmat on 2010-02-25
> **uncle-c said:**
> You can label ext2/2/4 partitions with e2label and NTFS ones with ntfsprogs.  Make sure the partitions are unmounted before you alter them.

I think the issue is more with the fact that the 'empty' partition is an extended partition rather than a primary one.

Unfortunately I do not know how to solve this. - Someone will though.

---

### Post by MelDJ on 2010-02-25
> **lotharmat said:**
> I think the issue is more with the fact that the 'empty' partition is an extended partition rather than a primary one.



yeah. thats what it is! sorry if i wasn't thorough (not very good at this)

---

### Post by oldfred on 2010-02-25
You could move or delete swap so the space is at the end of the extended then shrink the extended partition to make the space outside the extended. Leave enough room in the extended to recreate swap. This will break grub and fstab as the partition numbers and UUIDs will change maybe not for root but definitely for swap. Use a liveCD to edit fstab with the new UUIDs and reinstall grub. 

Not sure it is worth all the work?
Does it have to be a primary? Windows just about requires primary partitions but linux and data partitions can be logical.

---

### Post by MelDJ on 2010-02-26
i am trying to install freebsd. but somehow the empty partition doesn't show up in fdisk. hence i believe it must be made a primary partition.

---

### Post by plucky on 2010-02-26
> **MelDJ said:**
> i am trying to install freebsd. but somehow the empty partition doesn't show up in fdisk. hence i believe it must be made a primary partition.

That is because it doesn't have a filesystem.
And inside the extended partition it will be a logical partition.

You have to specify within gparted what filesystem  you require the un-allocated space to be.Also you have to un-mount the swap partition before it will allow you to do anything with the extended partition.

Boot the Live CD and run gparted
Right click on the swap partition and select swapoff.
Right click on the un-allocated space and select new.
Set the partition file system e.g ext2/3/4 or ntfs or fat
Click on apply.


Good Luck

---

