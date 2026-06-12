---
title: "Software RAID on RAW disks"
date: 2009-08-12
forum: General Help
---

### Post by buchan on 2009-08-12
So I upgraded to 9.04 on my home server yesterday and lost my /home array.  (3TB RAID5)

I was able to recover the array and get the data backed up to an external drive so that's all good.  I think the problems were caused because I added the array after I originally installed Ubuntu and never updated the /etc/mdadm/mdadm.conf file with the new array information.  

Anyhow, after figuring out how to get rid of and re-create the array I ended up building the new array on the raw disks instead of partitioning them, setting the partition to FD and then telling mdadm to use the partitions.  

so instead of having a /proc/mdstat file that looks like this:
```
md2 : active raid5 sdd1[3] sdc1[2] sdb1[1] sda1[0]
      2930287488 blocks level 5, 64k chunk, algorithm 2 [4/4] [UUUU]

```
My mdastat looks like this:
```
md2 : active raid5 sdd[3] sdc[2] sdb[1] sda[0]
      2930287488 blocks level 5, 64k chunk, algorithm 2 [4/4] [UUUU]

```
Notice that the sd* drives are not partitioned and I am just using the drive without any partition info.

Has anyone else tried this before?  Is there any reason I need to partition the drives if I am using the whole thing anyways?
Are there any pitfalls if something goes wrong?

Thanks

---

