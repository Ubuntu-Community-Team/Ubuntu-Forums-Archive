---
title: "Can't resize partition"
date: 2010-05-08
forum: General Help
---

### Post by mihai722 on 2010-05-08
I've been trying to resize my root partition with gparted. I resize a ntfs partition to get more freespace available and I got 30GB of freespace and when I try to resize my root partition (unmounted) I can't do it, it's like I don't have any freespace. Any solutions?

---

### Post by ambdeep on 2010-05-08
i don think you can resize a partition without formatting it....try taking a backup then delete your partition and create a new one....

---

### Post by Lucky75 on 2010-05-08
> **ambdeep said:**
> i don think you can resize a partition without formatting it....try taking a backup then delete your partition and create a new one....

No, that's not true, you can.

Where is your partition located? At the beginning of the disk? Do you have free space directly to the right of it? If not, I'm pretty sure you have to shift everything over, shrinking your other partitions which are in the way in the process. It will take a while. It'd not like NTFS where you can grow or shrink it wherever you feel like.

---

### Post by lmarmisa on 2010-05-08
GParted is a tools that is able to resize partitions (ext4, ext3, ext2 or ntfs) but I think that you will need to start your system from a Ubuntu LiveCD if you wish to resize the root partition of your HDD.

A previous backup is very convenient. I recommend you [http://clonezilla.org/](http://clonezilla.org/)

Best regards,

Luis

---

### Post by Luftfuß on 2010-05-08
If the partition you shrank is in front of/before the partition you are expanding then you need to move the partition first so that the free space appears after the partition you want to expand.

---

### Post by mihai722 on 2010-05-08
> **Lucky75 said:**
> No, that's not true, you can.

Where is your partition located? At the beginning of the disk? Do you have free space directly to the right of it? If not, I'm pretty sure you have to shift everything over, shrinking your other partitions which are in the way in the process. It will take a while. It'd not like NTFS where you can grow or shrink it wherever you feel like.

Yes, you are right, I don't have free space directly to the right of my partition, so I need to make a backup and then delete it and create another one ?

---

### Post by Lucky75 on 2010-05-08
> **mihai722 said:**
> Yes, you are right, I don't have free space directly to the right of my partition, so I need to make a backup and then delete it and create another one ?



You *can* do it on the fly, and just move everything over, but it would probably be a good idea to make a backup first.

---

