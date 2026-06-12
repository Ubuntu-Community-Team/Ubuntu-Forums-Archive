---
title: "Merge Partition..."
date: 2010-07-01
forum: General Help
---

### Post by dtrot55 on 2010-07-01
Hello,

I current have a dual booting laptop that I want to go strictly to a single boot ubuntu with windows virtual boxed.  I was wondering if someone could kind of walk me through how to merge my current windows partition with my ubuntu partition.  I haven't really done much hard drive partitioning in a Linux environment..so i dont want to screw up my linux install or my GRUB menu etc...

Any help much appreciated.

Thanks!

---

### Post by celldweller1591 on 2010-07-01
Just goto gparted in ubuntu and unmount the windows partitions(ntfs or fat32)and delete them. Remake partitions and select type as ext4 and all your partitions will be ubuntu based. Everything will be fine. No damage to grub at all :D Do you want to increase /home or /root partition size ??

---

### Post by dtrot55 on 2010-07-01
Just want to give my full hard drive to ubuntu...and not have to deal with windows at boot...I only really need windows for photoshop...I know there is GIMP..but GIMP gets annoying after awhile...and also if i ever want to dump windows in the future on this computer it will be easier

---

### Post by dtrot55 on 2010-07-02
I deleted the windows partition and then formatted in ext4..but that didn't merge the partitions...I want the whole harddrive dedicated and not split up into 2 partitions...is there a way to merge in gparted or something else?

---

### Post by Bucky Ball on 2010-07-02
WARNING: Before resizing any windows partitions (rather than delete them) DEFRAG! (This doesn't apply to EXT partitions).

---

### Post by dtrot55 on 2010-07-02
Hmmm Guess I might as well just pop in a disc and re-install ubuntu using the whole hard drive

---

### Post by Seanlol on 2010-07-02
> **dtrot55 said:**
> Hmmm Guess I might as well just pop in a disc and re-install ubuntu using the whole hard drive

No, no, no. You can do this easily. You don't need to actually reformat the partition you just deleted, doing so will just re-create a separate partition. You need to delete it so you have unallocated space, then move and extend the Ubuntu partition as needed. Formatting the partition will simply give you two EXT4 partitions.

--_Create a backup unless data integrity is not that important to you. Something could go wrong during this process_.--

1. Boot into Ubuntu via a Live CD. (GParted won't let you unmount your Ubuntu partition while you're actually using it.)

2. Open GParted 

3. Unmount and Delete your Windows partition.  (right click -> Unmount --- right click -> delete)

IF YOUR UBUNTU PARTITION IS AT THE END OF THE HDD:

4.  Move your Ubuntu partition all the way left and extend the partition to take up the entire drive. This is done by right clicking the partition, clicking "Resize/Move" and editing the partition so there is no unallocated space before it.

IF YOUR UBUNTU PARTITION IS AT THE BEGINNING OF THE HDD:

4. Simply extend the Ubuntu partition to take up the rest of the disk. This is done by right clicking the partition, and clicking "Resize/Move"

---

### Post by Bucky Ball on 2010-07-02
> **dtrot55 said:**
> Hmmm Guess I might as well just pop in a disc and re-install ubuntu using the whole hard drive

I would if you don't want windows and you have your important data backed up. Good idea.

---

