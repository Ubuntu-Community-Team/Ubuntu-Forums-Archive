---
title: "Slow raid 5 for some files"
date: 2011-02-23
forum: General Help
---

### Post by jackynix on 2011-02-23
I have a fileserver with a software RAID5 setup that does work relatively well, up to a certain point. It can handle 'most' reads and writes over LAN with 60 MB/sec, wich is sufficient imo.

But then, for certain files (>1 GB) I obtain read speeds as low as 2-3 MB/sec up to 10-11 MB/sec max. Moving those files to my win7 desktop pc and then moving them back to the ubuntu raid results in read/write speeds of 60 MB/sec again.

The array is about 10% full (or 90% empty).
hdparm returns this for the array:
 Timing cached reads:   1878 MB in  2.00 seconds = 939.13 MB/sec
 Timing buffered disk reads:  474 MB in  3.01 seconds = 157.62 MB/sec

I read some threads about low speed with RAID5, but this is different. I have good speeds, but not always.

So, what happens here?

My specs:
Ubuntu 10.10 64bit (desktop)
1 x SSD OCZ VERTEX 2 40GB (os)
3 x WD GREEN 2TB (soft RAID5)
ext3
samba

---

### Post by YesWeCan on 2011-02-23
Does this slowness only happen during LAN reads? If you were to copy the same file to the SSD would it also be slow?
When this happens are all big files affected or is it just some? Is it repeatable...are the affected files always affected (until you rewrite them)?

---

### Post by jackynix on 2011-02-23
LAN or to another internal drive doesn't make a difference. The same happens.

Below is repeatable:
- file moves from raid array to ssd with 5 MB/sec
- file moves back from ssd to raid array with 60-70 MB/sec
- file moves from raid array to ssd with 60-70 MB/sec

So, once I moved the file forward and back, the speed remains stable.

Those big files are downloaded iso's. Could it be possible that _concurrent downloading_ clutters the files too much?  (fragmentation) And moving them forward and back sort of sequentially re-arrange those files? (defragmentation)

---

### Post by Seq on 2011-02-23
> **jackynix said:**
> LAN or to another internal drive doesn't make a difference. The same happens.

Below is repeatable:
- file moves from raid array to ssd with 5 MB/sec
- file moves back from ssd to raid array with 60-70 MB/sec
- file moves from raid array to ssd with 60-70 MB/sec

So, once I moved the file forward and back, the speed remains stable.

Those big files are downloaded iso's. Could it be possible that _concurrent downloading_ clutters the files too much?  (fragmentation) And moving them forward and back sort of sequentially re-arrange those files? (defragmentation)

It could also be caching. "Free" memory is used to cache files, so if you access it again it won't have to re-read it from the disk. After the files are coped once, they are possibly still in cache, thus making the copy write-dependant, rather than read-dependant. How much memory do you have?

Not sure why it would take so long to read initially, though. If you're using ext4, it is supposed to have some better allocation mechanisms to limit fragmenting, so that shouldn't really be an issue. Typically writing to raid5 is slower than reading since you need to calculate a checksum..

---

### Post by YesWeCan on 2011-02-23
cat /proc/mdstat ?

If your raid were degraded I suppose some files would read fast and some very slow. Slow reads are <10% the speed of the fast ones *as if* the raid was having to reconstruct the files from parity. When writing the file afresh there is no reconstruction involved.

---

### Post by jackynix on 2011-02-23
It's not the ram. I have 2 GB and some 5 GB files can be read very fast.

> **YesWeCan said:**
> cat /proc/mdstat ?
```
 Personalities : [linear] [multipath] [raid0] [raid1] [raid6] [raid5] [raid4] [raid10]
  md0 : active raid5 sdd1[2] sdc1[1] sdb1[0]
  3907023872 blocks level 5, 64k chunk, algorithm 2 [3/3] [UUU]
```After some more google, imo, the problem is the download client I use. It downloads small chunks, and as I read somewhere, linux uses "sparse" files, that can be very much a problem when downloading multiple files concurrently. Even reserving the needed space in advance doesn't help apparently (only writing all zeros to initialise the needed space might help).

Now I'm going to download only 1 rather big file (no other concurrent downloads) and see what happens...

Also, should I think about using ext4 instead of ext3?

---

### Post by jackynix on 2011-02-25
After some testing, I can confirm that the slowness of the file system is caused by overactive _"sparse"_ functionality.

The download client has a setting to reserve the complete size of the file at initialization. Works well.

I don't know whether the file system itself can be tuned for better performance. Imo it should be fixed/tweaked in the file system itself, cause the workaround I did is just a workaround for that application. Other applications don't have a setting to reserve the space in one big zone.

- EDIT -

I think I shouted victory too soon.
Apparently, I have drives with the new 4k sectors and didn't align them properly (didn't know I had to). Have to start the partitions and raid all over again.

---

