---
title: "fdisk, partitions, hdds and terms of storage"
date: 2011-01-18
forum: General Help
---

### Post by michael.dobrovitsky on 2011-01-18
hello,
i have a question regarding how data is placed on a media,
for example the daily used hdd:
when we talk about storage we often speak in heads sectors and cylinders.

my question is if heads, sectors and cylinder is the true way data exists on a hdd platter?

lets take for example, disk_x
1000.2gb = 1000204886016 bytes
255 heads, 63 sectors/track 121601 cylinders.

fdisk -H 128 -S 32 /dev/disk_x
each cylinder will be shrank to 2097152bytes, number of cylinders will grow to 476934. but everything will be much more aligned and readable or there is something i don't know and i will loose almost half of the total sector count on the hdd cause 63-32=31.  i asked the partitioner just to use 32 sectors from each track and only 128 tracks of the cylinder.

or another example, if i have a cluster size of 4k.
why not making each track use 56 sectors or 7 clusters.
theoretically i have all files in my storage and each one of them occupies 14 clusters isn't it wiser to make it as described.

what happens when i invoke fdisk -h -s params?

what will be changed, the disc physically and the way it is accessed or only the partition table?

you probably asking your self what the hell does this dude wants?
so, i want to get maximum i/outputs and the widest bandwidth and the nicest readble partition tables and to understand better fdisk -H -S.

---

### Post by dandnsmith on 2011-01-18
> **michael.dobrovitsky said:**
> hello,
my question is if heads, sectors and cylinder is the true way data exists on a hdd platter?

lets take for example, disk_x
1000.2gb = 1000204886016 bytes
255 heads, 63 sectors/track 121601 cylinders.

fdisk -H 128 -S 32 /dev/disk_x
each cylinder will be shrank to 2097152bytes, number of cylinders will grow to 476934. but everything will be much more aligned and readable or there is something i don't know and i will loose almost half of the total sector count on the hdd cause 63-32=31.  i asked the partitioner just to use 32 sectors from each track and only 128 tracks of the cylinder.

or another example, if i have a cluster size of 4k.
why not making each track use 56 sectors or 7 clusters.
theoretically i have all files in my storage and each one of them occupies 14 clusters isn't it wiser to make it as described.

what happens when i invoke fdisk -h -s params?

what will be changed, the disc physically and the way it is accessed or only the partition table?

you probably asking your self what the hell does this dude wants?
so, i want to get maximum i/outputs and the widest bandwidth and the nicest readble partition tables and to understand better fdisk -H -S.

I strongly advise you to read the man pages for fdisk, and then give up the idea.

The CHS representation of the HDD is not a *real* view of the HDD organisation, based on the way some hardware/software combinations need to work. If you do a bit of reading you'll find that real tracks vary in length/content from middle to outside of the platter(s).

If you once adopt this sort of view, you take on the responsibility of overriding the natural way to access the HDD - together with whatever happens if/when you upgrade/change the OS you are using.

Have fun, and lots of luck

---

### Post by dandnsmith on 2011-01-18
Problems with server - caused double post

---

### Post by psusi on 2011-01-18
fdisk is about the only place that you ever see CHS and it has been meaningless for nearly 20 years.  Forget about it and just tell fdisk to switch to sector mode with the u command or switch.

Internally a disk still has them, but they are variable length and the computer does not know or care about their configuration.  That is left up to the logic on the drive.  Everything outside the drive uses LBA.

---

### Post by michael.dobrovitsky on 2011-01-18
read fdisk man pages and it doesn't describe much, i know that if i do fdisk /dev/drive new partition from start to end than it works. but i want to know how to make it so hdds will work best. so the thing that you two say is that 20 years ago chs was the scheme to address to the hdd but nowdays it's obsolete.
ok so after reading [http://en.wikipedia.org/wiki/Logical_block_addressing](http://en.wikipedia.org/wiki/Logical_block_addressing)
i understand that most hdds work like described above.

so now my question is, how do the file systems intersect with lba.
do the entire partition exist as one big array or each file sits as an array. how do clusters work if everything is a spread of arrays.

as i know each file inhabits atleast one cluster. why does each file needs 4k to exist. if i have 1k file it inhabits 4k cluster. why? i don't think that access time creation date and all other info grabs the other 3k.
i always thought the head moves track by track to read data, now i see that it reads data by blocks.
please help me to understand the fs to hardware connection or redirect me to some sort of theory on that matter. i know that it seems unnecessary but i need to know.
sorry if my english is bad.

---

### Post by psusi on 2011-01-18
> **michael.dobrovitsky said:**
> 
do the entire partition exist as one big array or each file sits as an array. how do clusters work if everything is a spread of arrays.

The disk is one big array of sectors.  The filesystem allocates them to files.

> **michael.dobrovitsky said:**
> as i know each file inhabits atleast one cluster. why does each file needs 4k to exist. if i have 1k file it inhabits 4k cluster. why?

Because your filesystem is using a 4k block size, so it allocates 4k at a time.

> **michael.dobrovitsky said:**
> i always thought the head moves track by track to read data, now i see that it reads data by blocks.
please help me to understand the fs to hardware connection or redirect me to some sort of theory on that matter. i know that it seems unnecessary but i need to know.
sorry if my english is bad.

Physically the drive head does still seek track by track, but how it does so is not known outside the drive itself.  The OS only tells the drive which sector to read/write; the drive itself figures out where that sector is.

---

### Post by psusi on 2011-01-18
*SMACKS the forums*

---

