---
title: "MDADM Raid 5 &gt; Raid 6 conversion error"
date: 2010-09-07
forum: General Help
---

### Post by soljin2000 on 2010-09-07
Hey I am converting my 
**raid 5 array with 7 1 TB drives**
in it to a
**raid 6 with 10 1 TB drives**

I have added the 3 new 1 TB drives and here is my MDADM output:
>           State : clean
 Active Devices : 7
Working Devices : 10
 Failed Devices : 0
  Spare Devices : 3

         Layout : left-symmetric
     Chunk Size : 64K

           UUID : 32962b85:88fd246e:ecb23616:6508cad3
         Events : 0.2263814

    Number   Major   Minor   RaidDevice State
       0       8       96        0      active sync   /dev/sdg
       1       8       32        1      active sync   /dev/sdc
       2       8       80        2      active sync   /dev/sdf
       3       8      112        3      active sync   /dev/sdh
       4       8       64        4      active sync   /dev/sde
       5       8        0        5      active sync   /dev/sda
       6       8       48        6      active sync   /dev/sdd

       7       8      160        -      spare   /dev/sdk
       8       8      144        -      spare   /dev/sdj
       9       8      128        -      spare   /dev/sdi


I am trying to run this command:
**mdadm --grow /dev/md0 --level=6 --raid-devices=10 --backup-file=/md0.backup**

I get this error:
**mdadm: Cannot set device size/shape for /dev/md0: Invalid argument**

I found an old post here:
**[http://www.issociate.de/board/post/455533/RAID6_mdadm_--grow_bug?.html](http://www.issociate.de/board/post/455533/RAID6_mdadm_--grow_bug?.html)**

Suggesting that if I stop and remove the array then run this series of commands:
> mdadm --stop /dev/md0
mdadm --remove /dev/md0
losetup -d /dev/loop1;losetup -d /dev/loop2;losetup -d /dev/ 
loop3;losetup -d /dev/loop4;losetup -d /dev/loop5
rm rd1 rd2 rd3 rd4 rd5

I can then perform the opertation successfully.

My question is:
[B]Is the method I found likely to work?
If so will I be able to recover/reassemble the array afterwards keeping all the data?
Is there a better solution?
I MUST keep all the data and can't transfer all of it off somewhere else.[/B]

PS the server in question is running **10.10**

Thanks for any help you can provide.

---

### Post by soljin2000 on 2010-09-08
Solution found.  That snip-it posted above has NOTHING to do with getting this grow to work.

1) Yes if you stop and remove an array you can reassemble it just fine with no data loss.

2) Stopping and starting the array is not the problem.  Ubuntu as of 10.10 still has mdadm 2.6.7 as it's most up to date version.  You have to HAND install a newer version of mdadm from here:

[http://packages.debian.org/squeeze/mdadm](http://packages.debian.org/squeeze/mdadm)

That will have what you need you can just wget that deb and run:

dpkg -i (the file you dled)

you will have to do some light reconfiguring then the grow command works perfectly.

---

