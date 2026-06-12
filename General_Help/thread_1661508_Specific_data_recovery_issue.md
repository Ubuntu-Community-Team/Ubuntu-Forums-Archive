---
title: "Specific data recovery issue"
date: 2011-01-06
forum: General Help
---

### Post by JMO707 on 2011-01-06
Today I messed up my disk. Basically I tried to move some free space with Gparted via live-cd between two system partitions.

Now, my partition table is broken and I have lost my data partition.

Let me show you:

[I]fdisk -lu
[/I]

```

Disk /dev/sda: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x8f800100

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          63      192767       96352+   7  HPFS/NTFS
/dev/sda2          206848    55298047    27545600    7  HPFS/NTFS
/dev/sda3        55298048    69138431     6920192   83  Linux
/dev/sda4        69143760   625153409   278004825    f  W95 Ext'd (LBA)
/dev/sda5        76550144   118493183    20971520   83  Linux
/dev/sda6       623048704   625141743     1046520   82  Linux swap / Solaris
```


```
TestDisk 6.11, Data Recovery Utility, April 2009
Christophe GRENIER <grenier@cgsecurity.org>
http://www.cgsecurity.org

Disk /dev/sda - 320 GB / 298 GiB - CHS 38913 255 63
Current partition structure:
     Partition                  Start        End    Size in sectors

 1 * HPFS - NTFS              0   1  1    11 254 51     192705 [System Rese
 2 P HPFS - NTFS             12 223 20  3442  36 50   55091200
 3 P Linux                 3442  36 51  4303 170 27   13840384
 4 E extended LBA          4304   0  1 38913 254 63  556009650
 5 L Linux                 4765   6 42  7375 219 12   41943040
   X extended             38782 250  1 38913  69 52    2093164
 6 L Linux Swap           38782 251 62 38913  69 52    2093040


[Quick Search]  [ Backup ]
                            Try to locate partition
```


I used testdisk to write the detected partition table to disk, but gparted wont see it. Furthermore, my interest is in recovering the data that was stored in partition /dev/sda4 
There must be a way to try that. Im running System Rescue Cd, and there is this tool, extundelete, but it says

*extundelete: failed to read-only open device "/dev/sda4": Error code 2133571364*

Wich procedure would you recommend me to at least do the best I could trying to recover my data?

Thanks in advance.-

---

