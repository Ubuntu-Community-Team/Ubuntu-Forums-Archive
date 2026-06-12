---
title: "Moving partition performance wise"
date: 2009-08-29
forum: General Help
---

### Post by nuclear216 on 2009-08-29
I've read on many occasions using that the external section of the hdd plate provide more performance than the inner sections.
It is reasonable because the same rotation makes more block spin under the hdd head.
is it true?

this hypothesis being accepted I have the following question about moving my partition.

I have a notebook with one hdd (sda)
When I installed ubuntu I had to keep the windows partition so I shrinked it by 10GB and I installed ubuntu, those block happened to be on the outer section of the disk (good!). 

I now want to delete the windows partition and use it as a data partition.

that's my partition table (arbitrary number):
blocks 0 to 100 Windows 
blocks 101 to 125 Swap
blocks 126 to 300 Ubuntu, mounted as /, it's ext3

I Intended to delete Windows partition and make it ext4 and put my data in it (video and music) keeping all the software data to Ubuntu Partition (in the outer disc)

If I mount the ext4 partition as home and put my whole home directory there will I move some software too? doesn't the home contains a lot of "system" files which are used by many many programs?
as I want to keep all the software in the Ubuntu partition I fear if I move the whole home directory I move some software too.

---

### Post by mike555 on 2009-08-29
It would be better IMHO to make the partition and just backup your /home to it (unless you really need the space) because your computer hard drive arm will be going back and forth between the partitions too much if you make it /home and might slow down performance (think how using a swap slows down a computer )

---

### Post by CatKiller on 2009-08-29
> **nuclear216 said:**
> is it true?

True, but largely not useful. Most hard drives have more than one platter. You won't actually know which sectors are at the outside of a given platter.

> 
If I mount the ext4 partition as home and put my whole home directory there will I move some software too? doesn't the home contains a lot of "system" files which are used by many many programs?

No. Your Home folder contains configuration files for many programs, but these are tiny and are unlikely to make that much difference to overall performance.

For that matter, even if you somehow manage to get the files you want to the outside of a platter, it won't make that much difference to performance. When files have been loaded for the first time they are kept in RAM as a file cache in case they are needed again. RAM access is significantly faster than hard drive access, wherever the data might be located on the platters.

---

### Post by blueridgedog on 2009-08-29
> **nuclear216 said:**
> I've read on many occasions using that the external section of the hdd plate provide more performance than the inner sections.
It is reasonable because the same rotation makes more block spin under the hdd head.
is it true?


All parts of the platter are moving at the same RPM.  I too have read that the outside is considered faster due to the linear speed, but I have never seen reports that show the difference.  Rather than try to get a fractional increase in performance, I would suggest a partitioning scheme that met your needs and was functional.  If you make your first partition /, then your system will theoretically start the install at the outside of the platter and should have the best chance of using any fractional speed increase to help in boot times. (I personally wouldn't factor it in).

---

