---
title: "Problem extending ext4 drive"
date: 2010-06-04
forum: General Help
---

### Post by typeslow on 2010-06-04
Hi, I just deleted my Windows partition and I'm trying to add the unallocated space to my existing ext4 partition and I don't know what the problem is. When I try to resize(in Gparted) it's only possible to decrease the size. Forgive the poor description, I'm ignorant about filesystems/partitioning and didn't want to play with a formatting tool on my main hard drive.

pic::
[[IMG]http://img143.imageshack.us/img143/7952/20100604110443.th.jpg[/IMG]](http://img143.imageshack.us/i/20100604110443.jpg/)




i'm trying to do this without formatting the whole drive, i have data on both 'new volume' and my ext4 partition that would be time consuming to backup

---

### Post by Leppie on 2010-06-04
when expanding partitions, the free space needs to be at the end of the partition you want to expand. the easiest thing to do would be to format the free space to ext4 and create a new mount point for it.

---

### Post by TheDesertDragon on 2010-06-04
Can't you create a new partition, move all your stuff over, delete the old partition, and expand the new partition? Just a thought! :)

---

### Post by dcstar on 2010-06-05
> **typeslow said:**
> Hi, I just deleted my Windows partition and I'm trying to add the unallocated space to my existing ext4 partition and I don't know what the problem is. When I try to resize(in Gparted) it's only possible to decrease the size. Forgive the poor description, I'm ignorant about filesystems/partitioning and didn't want to play with a formatting tool on my main hard drive.

i'm trying to do this without formatting the whole drive, i have data on both 'new volume' and my ext4 partition that would be time consuming to backup

You have not deleted any partition according to that picture. It shows a mounted NTFS partition inside the Extended partition.

You must unmount all partitions inside an Extended Partition before making any changes to that partition.

---

### Post by Leppie on 2010-06-05
> **dcstar said:**
> You have not deleted any partition according to that picture. It shows a mounted NTFS partition inside the Extended partition.
there's about 128gig's of unallocated space before the extended partition ;)

---

### Post by Barafu Albino Cheetah on 2010-06-05
Did anybody of you watch his screenshot?
You have logical volumes, pal. It means you have your partition wrapped into extended partittion by name of sda2. 
You must first resize extended partition, reboot, that resize yours. 
After resizing partition that contains you /boot folder you will have to reinstall bootloader. Make sure you know how.

---

### Post by Leppie on 2010-06-05
> **Barafu Albino Cheetah said:**
> Did anybody of you watch his screenshot?
you may want to reread the posts...

---

### Post by Barafu Albino Cheetah on 2010-06-05
> **Leppie said:**
> you may want to reread the posts...
I had. But the problem is so obvious.

---

### Post by Leppie on 2010-06-05
> **Barafu Albino Cheetah said:**
> I had. But the problem is so obvious.
well, that's why i suggested to create a mount point. messing around with the extended partition will probably only cause data-loss.

---

### Post by Barafu Albino Cheetah on 2010-06-05
> **Leppie said:**
> well, that's why i suggested to create a mount point. messing around with the extended partition will probably only cause data-loss.
Topicstarter asked how to resize partition, and you, in fact, said he should format it all anew. I think he is able to do it without our guidance. 
Resizing extended partition with gparted is perfectly safe.

---

