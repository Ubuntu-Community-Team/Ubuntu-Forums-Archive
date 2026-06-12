---
title: "Any way to do this (advanced partitioning)"
date: 2011-08-12
forum: General Help
---

### Post by pqwoerituytrueiwoq on 2011-08-12
I am getting a 500gb hdd (1 disk 2 heads)
i know there is a round to cylinders option but i would like to round to platter
i would like my extended partition to be on one side of the disk and the rest to be on the other side of the disk
i think it would reduce the seek time this way and increase throughput during piratical use 
i assume the heads function independently

---

### Post by dcstar on 2011-08-13
> **pqwoerituytrueiwoq said:**
> I am getting a 500gb hdd (1 disk 2 heads)
i know there is a round to cylinders option but i would like to round to platter
i would like my extended partition to be on one side of the disk and the rest to be on the other side of the disk
i think it would reduce the seek time this way and increase throughput during piratical use 
i assume the heads function independently

Your assumptions are totally wrong.

---

### Post by YesWeCan on 2011-08-13
No, the heads are normally all on the same pivoted head stack, like the prongs of a fork. It would be mechanically impractical to have independent head movements. Theoretically, I suppose a disk could have two head stacks but I have not heard of such a thing. If you want to increase performance use two disks or use an SSD.

---

### Post by Bucic on 2011-08-13
You can use two other methods:
- shortstroking (packing related data close to each other)
- taking advantage of outer tracks (first partitions) yielding over 2x as much performance compared to inner tracks (last partitions).

The only tool that allows to fully take advantage of the two I know is UltimateDefrag 3 [http://www.disktrix.com/](http://www.disktrix.com/) EDIT: **Ah, I forgot it's not available for Linux, sorry!**

[http://www.disktrix.com/images/udscreens/defraggeddisk800.jpg](http://www.disktrix.com/images/udscreens/defraggeddisk800.jpg)

You can partially take advantage of the two with just smart partitioning... [http://ubuntuforums.org/showthread.php?t=1687792](http://ubuntuforums.org/showthread.php?t=1687792)

[IMG]http://i17.photobucket.com/albums/b68/Bucic/ubuntuforumsorg/linux_partitions_custom-1.jpg[/IMG]


**All that said my advice is to ditch HDD. Instead of wasting your time to improve its performance (and to maintain it!) just buy a 30 GB SSD for like $100, and a HDD for non performance critical data.**

---

### Post by pqwoerituytrueiwoq on 2011-08-13
"- taking advantage of outer tracks (first partitions) yielding over 2x  as much performance compared to inner tracks (last partitions)."
that is what i am going for
if i can place my stuff so i can use both outer edges i should get better performance than just one outer edge

---

### Post by YesWeCan on 2011-08-13
A half-baked musing: I wonder what performance increase you would get if you could arrange a RAID0 between heads? In one rotation of the disk you would read twice as much data from contiguous file(s). Might be limited by the sustained transfer of the disk drive. Hmm.

---

### Post by pqwoerituytrueiwoq on 2011-08-14
> **YesWeCan said:**
> A half-baked musing: I wonder what performance increase you would get if you could arrange a RAID0 between heads? In one rotation of the disk you would read twice as much data from contiguous file(s). Might be limited by the sustained transfer of the disk drive. Hmm.
if possible it would need to be on the firmware of the drive and it would look like one drive to apps which you could raid (double layer raid FTW)

---

### Post by pqwoerituytrueiwoq on 2011-08-15
> **Bucic said:**
> **All that said my advice is to ditch HDD. Instead of wasting your time to improve its performance (and to maintain it!) just buy a 30 GB SSD for like $100, and a HDD for non performance critical data.**
i am using a 16 gig ssd for root for less than 1/2 that and i am using less than 1/2 the drive
my current hdd's peak speed is ~50 mbps wile my ssd gets 230-250
the new hdd is for space for virtual machines /home swap and /var
but if i can get the point where it switches to the other side i can double the size of the edge speed boost

---

