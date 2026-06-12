---
title: "Ubuntu 11.04 - Raid 5 (mdadm) Clunking?"
date: 2011-11-07
forum: General Help
---

### Post by idtjes3 on 2011-11-07
Hello Everyone,

  I'm still really new to Ubuntu (giving it a second shot) so please bare with me. I am experiencing a strange problem with the Raid 5 (4x2TB disks) I just built using mdadm. For some reason one or more of my dirves is making a clunking noise. Its not the high pitched, rapid, click of death but more a low cha-chunk, cha-chunk every few seconds or so. Think of the sound when a train goes by ( but not that loud obviously :) ) I believe the disk are all good as I just had them all running in soft Raid5 on window server 2003 without any issues.

  Last time I attempted a Raid 5 in Ubuntu, I would was getting the same noise roughly 12 hrs after start up. Now, this tends to happen right after I boot up. I remember reading something about the heads continually trying to park or something and that's what may be causing it. I've read some fix for that situation, but to be honest I don't feel safe hacking the system like that as I've read that bumping the system after applying that could result in disk damage (unless I can be reassured). 

  I have also tuned my raid's reserved block percentage to 0% using tune2fs since its just going to be a media storage drive if that has any baring on the situation. I haven't done anything else since the Raid just finished building this morning.

  Has anyone ever experienced this issue before? I'm not at my machine right now so I can't provide specifics at the moment, but I could post a few things later If I know what you'd need to see. Sorry for the novel and thanks !

- John

---

### Post by xrxca on 2011-11-13
The train analogy is pretty good, clickety clack, clickety clak, I am just working on setting up a RAID5 myself (4x2TB as well) and am getting the same kind of clunking.  I'm wondering if it has something to do with the parameters used to create the array, should I have used a bigger or smaller chunk size, software raid + filesystem tuning seems to be a pretty dark art.  I could find no decent sites that gave straightforward recommendations without the comments basically breaking down into a flame war)

The drives should be ok in my case as well, they came out of my old mythtv server which had them in as 2 raid 1 arrays, I figured since the new system is only around 10 times faster raid 5 would be ok (and I'd get more space) but the clunking leaves me worried about the drive longevity.

I'd pick up another pair of 2TB's but the price of drives just tripled overnight.

Performance is just fine with the raid 5, I have no idea exactly what the read/write speed is, but I've had 3 hd streams recording and 4 playing at the same time (family can't wait for this to take over from the old beast)

I doubt the tune2fs setting has much to do with it, I'm using XFS myself.

Anyone have any pointers?

```
/dev/md0:
        Version : 1.2
  Creation Time : Fri Nov 11 18:22:21 2011
     Raid Level : raid5
     Array Size : 5860532448 (5589.04 GiB 6001.19 GB)
  Used Dev Size : 1953510816 (1863.01 GiB 2000.40 GB)
   Raid Devices : 4
  Total Devices : 4
    Persistence : Superblock is persistent

    Update Time : Sun Nov 13 00:53:50 2011
          State : active
 Active Devices : 4
Working Devices : 4
 Failed Devices : 0
  Spare Devices : 0

         Layout : left-symmetric
     Chunk Size : 32K

           Name : mythtest:0  (local to host mythtest)
           UUID : 0231ddd3:cf6b17ba:b8c1eb4c:87d0089d
         Events : 20

    Number   Major   Minor   RaidDevice State
       0       8       17        0      active sync   /dev/sdb1
       1       8       33        1      active sync   /dev/sdc1
       2       8       49        2      active sync   /dev/sdd1
       3       8       65        3      active sync   /dev/sde1

```

---

### Post by idtjes3 on 2011-11-13
Hard drive price just recently spiked due to massive flooding in south east Asia. As for the clunking, its appeared to stop. Ive had my system on for 3 days straight now with now clunking. nNot sure if it makes a difference but I actually have files on there now ( about 8% full of a 5TB setup) so maybe the presence of files had something to do with it.  Anyways try that and good luck.

---

