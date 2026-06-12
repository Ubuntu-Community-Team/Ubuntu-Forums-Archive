---
title: "How to format the memory space which is unformatted one"
date: 2009-10-15
forum: General Help
---

### Post by mlinuxuser on 2009-10-15
I am using ubuntu 9.04. While Installing I left windows drives, and installed ubuntu using remaining memory space with the custom install option. I chosen for root,home, and left 5gb as unmodified( which I thought to create a new drive in windows os).But I  could not  create a new drive with that 5gb in windows. Is it possible to create a drive that should contain a ntfs file system which should be visible in windows and ubuntu also?

---

### Post by DeMus on 2009-10-15
> **mlinuxuser said:**
> I am using ubuntu 9.04. While Installing I left windows drives, and installed ubuntu using remaining memory space with the custom install option. I chosen for root,home, and left 5gb as unmodified( which I thought to create a new drive in windows os).But I  could not  create a new drive with that 5gb in windows. Is it possible to create a drive that should contain a ntfs file system which should be visible in windows and ubuntu also?

It looks to me you have the maximum of 4 primary partitions on your disk.
You should have made one extended partition, in which you created the partitions you need.

---

### Post by mlinuxuser on 2009-10-15
> **DeMus said:**
> It looks to me you have the maximum of 4 primary partitions on your disk.
You should have made one extended partition, in which you created the partitions you need.

Yes. What Should I do now? Is there any other way to create a such a partition ?

---

### Post by mlinuxuser on 2009-10-15
no other way to do this?

---

### Post by justleen on 2009-10-15
To get more partition then the 4 logical that you have, you will have to get rid off 1, then create an extended partition, which can hold the extra partitions..

If your at the (max) 4 logical partitions, there is no option to create more partitions. 
Perhaps another option is to boot a live cd and resize a partition to use the last 5 gb?

---

### Post by mlinuxuser on 2009-10-15
I dont have 4 partitions in ubuntu. Only two partitions root and home

---

### Post by justleen on 2009-10-15
And how many NTFS paritions?
can you post the output of ```
 cat /proc/partitions 
```

---

### Post by mlinuxuser on 2009-10-15
> **justleen said:**
> 

If your at the (max) 4 logical partitions, there is no option to create more partitions. 


I do have only 2 partitions

---

### Post by mlinuxuser on 2009-10-15
> **justleen said:**
> And how many NTFS paritions?
can you post the output of ```
 cat /proc/partitions 
```

  8        0   78150744 sda
   8        1   20482843 sda1
   8        2   14651280 sda2
   8        3          1 sda3
   8        4   22523098 sda4
   8        5    7815591 sda5
   8        6     995998 sda6
   8        7    4996183 sda7

---

### Post by justleen on 2009-10-15
> **mlinuxuser said:**
> 8        0   78150744 sda
   8        1   20482843 sda1
   8        2   14651280 sda2
   8        3          1 sda3
   8        4   22523098 sda4
   8        5    7815591 sda5
   8        6     995998 sda6
   8        7    4996183 sda7


You have 2 primary partitions (sda1 and sda2), and 1 extended (sda3) which contains the maximum 4 partions again (sda4 to sda7)

if the 5 GB unpartitioned spaced is within the extended partition, you cannot create a new partition.

---

### Post by mlinuxuser on 2009-10-15
> **justleen said:**
> You have 2 primary partitions (sda1 and sda2), and 1 extended (sda3) which contains the maximum 4 partions again (sda4 to sda7)

if the 5 GB unpartitioned spaced is within the extended partition, you cannot create a new partition.


How can I know that whether that 5gb is within the extended partition or not?

---

### Post by justleen on 2009-10-15
use a GUI partition editor, like gparted.

---

### Post by StuartN on 2009-10-15
> **mlinuxuser said:**
> no other way to do this?

You can boot from a live CD (the Ubuntu Install CD) so that all your partitions are unmounted and run GParted. Then you can enlarge whichever partition is next to the unallocated space - at least that way you can use the space.

Don't forget that you have a swap partition, so you have "only two partitions", / and /home, plus the swap.

---

### Post by mlinuxuser on 2009-10-15
Thanks for the suggestions .I will try and post afterwards :)

I have another problem. Is it possible to view the ubuntu home folder from windows os?

---

### Post by az on 2009-10-15
> **mlinuxuser said:**
> 

I have another problem. Is it possible to view the ubuntu home folder from windows os?

[http://www.fs-driver.org/](http://www.fs-driver.org/)

---

