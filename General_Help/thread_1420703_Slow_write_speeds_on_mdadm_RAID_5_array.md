---
title: "Slow write speeds on mdadm RAID 5 array"
date: 2010-03-03
forum: General Help
---

### Post by bbm5 on 2010-03-03
I have a 4 drive RAID 5 array set up using mdadm. The system is stored on a seperate physical disk outside of the array. 

When reading from the array its fast but when writing to the array its extremely slow, down to 20MB/Sec compared to 125MB/Sec reading. It does a bit then pauses, then writes a bit more and then pauses again and so on.

The test i did was to copy a 5GB file from the RAID to another spare non-raid disk on the system average speed 126MB/s. Copying it back on to the RAID (in another folder) the speed was 20MB/s.

Raid info as follows....

        Version : 00.90
  Creation Time : Tue Mar  2 18:14:37 2010
     Raid Level : raid5
     Array Size : 2930279808 (2794.53 GiB 3000.61 GB)
  Used Dev Size : 976759936 (931.51 GiB 1000.20 GB)
   Raid Devices : 4
  Total Devices : 4
Preferred Minor : 0
    Persistence : Superblock is persistent

    Update Time : Wed Mar  3 16:25:00 2010
          State : clean
 Active Devices : 4
Working Devices : 4
 Failed Devices : 0
  Spare Devices : 0

         Layout : left-symmetric
     Chunk Size : 64K

           UUID : f1d6880c:3cfd4cda:8ada4936:6770a6cd
         Events : 0.20

    Number   Major   Minor   RaidDevice State
       0       8        1        0      active sync   /dev/sda1
       1       8       17        1      active sync   /dev/sdb1
       2       8       65        2      active sync   /dev/sde1
       3       8       81        3      active sync   /dev/sdf1

The other thing is very slow several KB/s write speed copying from eSATA drive to the RAID.

---

### Post by bbm5 on 2010-03-03
Update....

installed iotop and monitored it while running the write test again. Every time there is a pause the kjournald process comes near the top of the list before dropping out once the pause is over. 

Sounds a bit of an inefficient way of updating the journal on the file system doesn't it? or is this a problem with my config?

---

### Post by rabbit20 on 2010-03-20
Having the same issue with mdadm raid 5 under Linux RAID...I am also using 4 drives (1TB each) all the drives are 7200 RPM drives. Right now I am writing at 8.6 MB per second and this is from my desktop to my Server that runs the raid and the Ethernet connection is a cross over cable from desktop to server.

---

### Post by Xurri on 2010-04-21
I've got the same problems with a raid 5. I'm using 4 drives, whereas each has ~100mb/s read and 80mb/s write speed sequentially. Benchmarks showed me that i get ~220mb/s read and ~10mb/s write speed. The first 700 mb of write are really fast (must be cached or something like that) but than it drops down to the mentioned 10mb/s. I have been looking often for a solution but I haven't been lucky so far. I would appreciate help.

---

### Post by Ipharus on 2010-04-24
At work i have setup a 3 (sata) disk mdadm RAID 5 with XFS filesystem (on a hardy server). I dont know if this system is vulnerable to this issue but it made me wonder. What file system do you guys use on your 4 disk RAID 5 systems? And what release of ubuntu?

---

### Post by bvanaerde on 2010-04-27
I think I'm having the same problem here. It doesn't happen all the time though, so I'm not sure what the problem is. I'll have to test more. Right now I'm performing e2fsck on the partition. How are you benchmarking the drives?

I've got a RAID5 setup with 4x 1TB drives, resulting in 3TB space. I had to make two partitions of both 1.5TB, because of the partition size restriction of EXT3.

---

### Post by Rickolati on 2011-03-24
Has anyone made any breakthrough on this? I am getting similar performance on my RAID.

~20Mbps write and ~80Mbps read..

I am hoping to improve this somehow! I have the chunk size at 512 and am using metadata 0.90

Any thoughts?

---

### Post by ziggo0 on 2011-03-31
Same problem here...brand new raid5 array, running terrible. 5x2tb WD Green drives, started out fine, about 100mb/s read/write, perfectly acceptable for gigabit LAN - then it slowed down to around 40 ~ 60mb/s.....then 10mb/s....maybe 500kb/s sometimes, other times 6mb/s (write, over a week). All disks checked out in WD extended, raid has been clean the entire time, no failures reported. 

From my research I haven't seen a single solution to this problem...it's pretty wide spread, even though this thread is old.

---

### Post by Rickolati on 2011-03-31
I have 4xWD Green 2Tb and 1xSeagate 2Tb

I found a few suggestions:

[LIST]
 tuning /sys/block/mdX/md/stripe_cache_size
[/LIST]
[LIST]
enable DMA, you can see the status with sudo hdparm /dev/hda
[/LIST]

I am weary of doing it on the live RAID as I have it filled to the brim and I am not confident that the changes does not have risk of data loss. It would be useful if anyone could comment on that??

The chunk size is also important but as far as I know can only be defined in building the RAID array. Mine is at 512kb.

What is you metadata version? Mine is 0.90. I don't think this can be changes after the RAID has been built.

Any suggestions on performance increases would be VERY useful!

---

### Post by jman177 on 2011-07-05
Thanks for the idea but I tried changing stripe_cache_size from default 256 to 8192 but it made no difference to my write speed of 11mb/s but it did increase my read speed a little.

I have not tried your second idea yet, did you manage to get a solution to this problem?

Also I am running WD20EARS (Green) drives in my ubuntu RAID5 array is that causing the issue & if so how can I fix it.

Also forgot to mention I am running Ubuntu 11.04 64 bit

Thanks

---

### Post by Rickolati on 2011-07-06
I have not implemented the change, like I said I was too scared to do it because of the amount of important data I have on there at the moment.

I was hoping for feedback from someone who has tried it, but that seems to hard info to come by :)

---

### Post by jman177 on 2011-07-07
I found a solution to my 10mb/s write speed it now runs at 40mb/s wrtie speed. Please find below my fix:-

(Plase do this when you can have a 12-24 hours downtime)

Go to "Disk Uti" disconnect any partions & do a "Check Array"

Another thing I noticed when doing a copy from Win7 to Ubuntu SMB share which is larger than the available space it will slow down till you have filled the completely filled the disk

(eg. Had it start at 60mb/s & drop to 1mb/s and then Win7 gave me the no space message after about 10 minutes on a 2GB file)

If you change your cache from 256 to 8192 this will increase ytour write speed from 40mb/s to about 60mb/s or more.

Please let me know if this helps

---

