---
title: "9TB RAID5 only showing 4.1TB"
date: 2011-05-23
forum: General Help
---

### Post by JohnnyC35 on 2011-05-23
I have created a 9TB raid from 4 1.5TB drives and 3 2TB drives (1.6 and .4 partition). I thought it would be a 9TB partition, and Ubuntu says it is a 9TB partition except when looking at what drive space is left. Nautilus' Properties and System Monitor both say that the raid is 4.1TB with 1TB free but Disk Utility and Nautilus say it is a 9TB RAID. very odd. I have tried checking the raid and the xfs file system. no errors.

here is from watch cat /proc/mdstat
```

md1 : active raid5 sdg1[5] sdf1[6] sde1[4] sda[0] sdd[3] sdb[2] sdc[1]
      8790830976 blocks level 5, 4k chunk, algorithm 2 [7/7] [UUUUUUU]

```

    sudo mdadm --grow /dev/md1 --size=max
doesn't give me any errors but does't fix this either

and here's md1's details
```

john@JCMedia ~ $ sudo mdadm --detail /dev/md1
/dev/md1:
        Version : 00.90
  Creation Time : Mon Jan 24 20:00:46 2011
     Raid Level : raid5
     Array Size : 8790830976 (8383.59 GiB 9001.81 GB)
  Used Dev Size : 1465138496 (1397.26 GiB 1500.30 GB)
   Raid Devices : 7
  Total Devices : 7
Preferred Minor : 1
    Persistence : Superblock is persistent

    Update Time : Mon May 23 17:44:14 2011
          State : clean
 Active Devices : 7
Working Devices : 7
 Failed Devices : 0
  Spare Devices : 0

         Layout : left-symmetric
     Chunk Size : 4K

           UUID : 45ce3b6c:16704cc3:f232bd12:bb8df5df (local to host JCMedia)
         Events : 0.99372

    Number   Major   Minor   RaidDevice State
       0       8        0        0      active sync   /dev/sda
       1       8       32        1      active sync   /dev/sdc
       2       8       16        2      active sync   /dev/sdb
       3       8       48        3      active sync   /dev/sdd
       4       8       65        4      active sync   /dev/sde1
       5       8       97        5      active sync   /dev/sdg1
       6       8       81        6      active sync   /dev/sdf1

```

Any thoughts as to where I should go from here?

---

### Post by prodigy_ on 2011-05-24
What does **df -h** say?

---

### Post by crispy_420 on 2011-05-24
Don't know if this helps but it may be a limitation based on block size if you read this:

[http://www.linuxforums.org/forum/suse-linux/158973-4-terabyte-hard-drive-limit.html](http://www.linuxforums.org/forum/suse-linux/158973-4-terabyte-hard-drive-limit.html)

Maybe a hardware limitation is possible too.

---

### Post by JohnnyC35 on 2011-05-24
df -h says
/dev/md1              4.1T  3.0T  1.2T  72% /media/RAID5

XFS shouldn't be bothered by the limit. 8 exobytes :)

Its a software raid so I wouldn't think motherboard limitations would be an issue.

hmmm

---

### Post by YesWeCan on 2011-05-24
I don't know. 
All 6 drives were formatted XFS and then you partitioned 2 of them and then you created the mdadm RAID5 and then you formatted the RAID5 as XFS?
Is that right?

A little more detail about your system?
Are all 9TB usable?

I would be inclined to try to reproduce the symptoms in VirtualBox. It may be a software fault in Nautilus/System Monitor or some common utility they employ.

---

### Post by JohnnyC35 on 2011-05-24
My system has a Ion-itx f-e board with a 4 port sata pci-e attatched. With 3 2TB drives, with a 1.6Tb partition, and a .4 partition, and 4 1.5TB. I had the 4 1.5's in a 4.5TB xfs raid and added the 3 2's later.
As far as I know all 9TB isn't useable but I don't have over 4TB of data yet. I was going to duplicate the stuff I have on there, it'll take several hours. Right now I am trying removing a drive, adding it back and see what happens. My next step will be to remove 3 of the drives, make a new RAID5, and then copy over the data and re-add the drives to the new array and see if that works. 
not really sure why it is happening, and Google isn't providing much info. We shall see :)

---

### Post by YesWeCan on 2011-05-24
Peppermint One OS - interesting. Never heard of it but I am installing it to have a look.

This may be a dumb question, but you did remember to resize the partition after you added the extra drives...that is you need to extend the formatted partition too. I only mention this because the available space has not changed from the original RAID5.

---

### Post by JohnnyC35 on 2011-05-24
I found Peppermint One about a year ago, when I was trying to find a low over head OS. I have added a few gnome features to it but it is mostly an LXDE system. runs nice and quick.

I have run "mdadm --grow /dev/md1 --size=max" but that didn't seem to do anything.

I found here: [http://www.howtoforge.com/how-to-resize-raid-partitions-shrink-and-grow-software-raid](http://www.howtoforge.com/how-to-resize-raid-partitions-shrink-and-grow-software-raid)
that I should run "resize2fs /dev/md1"; this could be because I am currently re-adding a hard drive but here's the output

```

john@JCMedia ~ $ resize2fs /dev/md1
resize2fs 1.41.11 (14-Mar-2010)
open: Permission denied while opening /dev/md1
john@JCMedia ~ $ sudo resize2fs /dev/md1
[sudo] password for john: 
resize2fs 1.41.11 (14-Mar-2010)
resize2fs: Bad magic number in super-block while trying to open /dev/md1
Couldn't find valid filesystem superblock.

```

---

### Post by YesWeCan on 2011-05-24
Yes, this will be the problem. The growing of the array does not automatically grow the XFS filesystem. This is why mdadm claims it is a 9GB RAID but Nautilus says there is only a 4GB partition.

You may need **xfs_growfs** [http://linux.die.net/man/8/xfs_growfs](http://linux.die.net/man/8/xfs_growfs)
I have never used XFS so I am not familiar with it. resize2fs is only for ext filesystems.

I've just been playing with Peppermint in VirtualBox. It seems very fast. I gather it is a Ubuntu variant, slimmed down a lot.

---

### Post by JohnnyC35 on 2011-05-24
HA!
xfs_growfs was the trick. I was able to do it while resyncing and it only took a few minutes. It is now showing 8392.9GB in System Monitor, 8.19T in GParted, and 8.2T via df -h. That is much more inline to what it should be.I will have to keep that mind :)
Thanks a bunch!

Peppermint is built on the 2-year stable of Ubuntu, slimmed down quite a bit. Peppermint Ice is slimmed down even more. Their primary focus is web/cloud based applications but I have adjusted it to be more offline.

---

### Post by YesWeCan on 2011-05-24
You are welcome. I just finished recreating your RAID5 and enlarged it and used xfs_growfs to grow the filesystem. :)

Don't forget to mark this thread as solved in "thread tools" above.

---

