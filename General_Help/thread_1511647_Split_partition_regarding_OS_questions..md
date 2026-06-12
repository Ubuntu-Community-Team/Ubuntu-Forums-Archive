---
title: "Split partition regarding OS questions."
date: 2010-06-17
forum: General Help
---

### Post by es305 on 2010-06-17
Just partitioned my computer to have windows and Linux. When I boot up I'm given 2 choices of 
Ubuntu to boot and was wondering if I did it incorrectly. Was also wondering what NTFS, Extended, ext4 and Swap meant?.  Thanks in advance.

-eS

---

### Post by dcstar on 2010-06-17
> **es305 said:**
> Just partitioned my computer to have windows and Linux. When I boot up I'm given 2 choices of 
Ubuntu to boot and was wondering if I did it incorrectly. Was also wondering what NTFS, Extended, ext4 and Swap meant?.  Thanks in advance.

-eS

You have a normal Ubuntu selection and a "Recovery" selection, when you get new kernels you will see boot entries for those as well.

You can search out definitions for all of those terms.

---

### Post by es305 on 2010-06-17
Sorry, what I meant was on boot up it shows two Ubuntu choices and two recoveries.

---

### Post by WorMzy on 2010-06-17
You may have two kernels installed. Grub will detect both of them and create a normal entry and a recovery entry for each of them. You can probably edit the grub files to make it only list the most recent kernel, but I couldn't tell you how you'd go about doing that, I don't use Grub 2.

NTFS, Extended, ext4 and Swap are all partition types. EXT and Swap are two types of Linux partitions, NTFS is a Windows partition, Extended is a special partition that just holds other partitions. Read about partitions here: [http://en.wikipedia.org/wiki/Disk_partitioning](http://en.wikipedia.org/wiki/Disk_partitioning)

---

### Post by es305 on 2010-06-22
Thanks Wormz :KS

---

