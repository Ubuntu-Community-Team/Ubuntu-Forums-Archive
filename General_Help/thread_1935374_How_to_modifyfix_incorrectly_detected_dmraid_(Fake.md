---
title: "How to modify/fix incorrectly detected dmraid (FakeRaid) RAID 10 array."
date: 2012-03-04
forum: General Help
---

### Post by okamiueru on 2012-03-04
I'm trying to get dmraid to properly detect an existing RAID 10 array, which is working fine within windows 7. In summary, the drive setup and bios partitioning is as following:

 - 2 x SSD (120 GB), RAID 0.
    Partitioned into 180 GB (win7) and 58 GB (Ubuntu).
 - 4 x HDD (2 TB), RAID 1+0.

The Ubuntu installation itself is on a partitioned striped disk pair, and works fine. These correspond to the following lvm's (I've taken the liberty to format the data for readability):

```

#$ sudo dmsetup info /dev/dm-{1,2,3,4,5}
|----------+--------+---------------+-----------+----------+--------|
| dev/dm-0 | ubuntu | pdc_hjijcjji  | container |          | 58 GB  |
| dev/dm-1 | ubuntu | pdc_hjijcjji1 | /         | ext4     | 54 GB  |
| dev/dm-2 | ubuntu | pdc_hjijcjji2 |           | extended | 4.3 GB |
| dev/dm-3 | win 7  | pdc_fjhhdeeg  | container |          | 180 GB |
| dev/dm-4 | ubuntu | pdc_hjijcjji5 |           | swap     | 4.3 GB |
| dev/dm-5 | win 7  | pdc_fjhhdeeg1 |           | ntfs     | 180 GB |
|----------+--------+---------------+-----------+----------+--------|

```

The Raid 10 array consists of four 2TB disks, and give a resulting 4TB array. It seems as if dmraid is aware of this array, given the following output:

```

#$ sudo dmraid -r
|----------+--------+------------------+--------+---------+----------------+---------|
| Device   | Format | Name             | Type   | Status? | Size (sectors) | ?       |
|----------+--------+------------------+--------+---------+----------------+---------|
| /dev/sdf | pdc    | pdc_fjhhdeeg     | stripe | ok      |      175781248 | data@ 0 |
| /dev/sde | pdc    | pdc_fjhhdeeg     | stripe | ok      |      175781248 | data@ 0 |
| /dev/sdd | pdc    | pdc_bjibibahah-1 | stripe | ok      |     1758766336 | data@ 0 |
| /dev/sdc | pdc    | pdc_bjibibahah-1 | stripe | ok      |     1758766336 | data@ 0 |
| /dev/sda | pdc    | pdc_bjibibahah-0 | stripe | ok      |     1758766336 | data@ 0 |
| /dev/sdb | pdc    | pdc_bjibibahah-0 | stripe | ok      |     1758766336 | data@ 0 |
|----------+--------+------------------+--------+---------+----------------+---------|

```

Which throws me off a bit, since I'd expect the array, pdc_hjijcjji, to show up here as well. Perhaps, since it's a partition within a striped disk, it is included within pdc_fjhhdeeg. In any case, the striped array is running fine, so I'm not too worried about it.

Running dmraid -s, it shows up:

```

#$ sudo dmraid -s
|-----------+----------------+--------------+--------------|
| Name      | pdc_bjibibahah | pdc_fjhhdeeg | pdc_hjijcjji |
|-----------+----------------+--------------+--------------|
|           |       Superset |   Active Set |   Active Set |
| Size (-h) |       1.677 TB |     167.6 GB |      54.0 GB |
| Size      |     3517532672 |    351562496 |    113281024 |
| Stride    |            128 |          128 |          128 |
| Type      |         raid10 |       stripe |       stripe |
| Status    |             ok |           ok |           ok |
| Subsets   |              2 |            0 |            0 |
| Devs      |              4 |            2 |            2 |
| Spares    |              0 |            0 |            0 |
|-----------+----------------+--------------+--------------|
# Size is in blocks of 512 bytes.

```

Where pdc_bjibibahah seems to correspond to my Raid10 array, except that has a weird size (1.677 TB, as apposed to approx 4TB). Trying to activate this using dmraid -ay results in a 1.677 TB device with unallocated data, which I find reasonable as it's not the correct configuration.

Running "sudo dmraid -s -si" on the bjibibahah array:
```

#$ sudo dmraid -s -si
|-----------+----------------+------------------+------------------|
| Name      | pdc_bjibibahah | pdc_bjibibahah-0 | pdc_bjibibahah-1 |
|-----------+----------------+------------------+------------------|
|           |       Superset |           Subset |           Subset |
| Size (-h) |       1.638 TB |         1.638 TB |         1.638 TB |
| Size      |     3517532672 |       3517532672 |       3517532672 |
| Stride    |            128 |              128 |              128 |
| Type      |         raid10 |           stripe |           stripe |
| Status    |             ok |               ok |               ok |
| Subsets   |              2 |                0 |                0 |
| Devs      |              4 |                2 |                2 |
| Spares    |              0 |                0 |                0 |
|-----------+----------------+------------------+------------------|

```

I've tried configuring the arrays manually, but with no success, and the man page isn't proving all too helpful either. If anyone has a suggestion as to how to configure dmraid, or to convince it to change the configuration of the RAID10 array, I would be really grateful.

Here are a few outputs, should it be relevant:
```

$ sudo dmraid -V
dmraid version:		1.0.0.rc16 (2009.09.16) shared
dmraid library version:	1.0.0.rc16 (2009.09.16)
device-mapper version:	4.20.0

$ sudo dmsetup --version
Library version:   1.02.48 (2010-05-20)
Driver version:    4.20.0

$ uname -srvm
Linux 3.0.0-16-generic #28-Ubuntu SMP Fri Jan 27 17:44:39 UTC 2012 x86_64

```

Also, the BIOS raid setup of the RAID10 array match the following disks within ubuntu:
```

|---------+------------+--------------|
| Port:ID | Assignment | OS Disk Name |
|---------+------------+--------------|
|   01:01 | LD 1-1     | /dev/sda     |
|   02:01 | LD 1-2     | /dev/sdb     |
|   03:01 | LD 1-3     | /dev/sdc     |
|   04:01 | LD 1-4     | /dev/sdd     |
|---------+------------+--------------|

```

---

### Post by okamiueru on 2012-03-05
Anyone? I'll gladly check or try out anything. I have a backup of the 4 TB array, so it wouldn't be too horrible should it become corrupted.

---

### Post by okamiueru on 2012-03-18
A subtly disguised bump, but: Could someone point me to the direction where I might get some answers, or some better documentation as to how to remove established raid mappings, than the dmraid man page?

---

