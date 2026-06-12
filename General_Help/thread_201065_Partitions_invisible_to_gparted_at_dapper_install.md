---
title: "Partitions invisible to gparted at dapper install"
date: 2006-06-21
forum: General Help
---

### Post by JohanSwe on 2006-06-21
This is so very strange. The partitioning failed during a previous install and now when I have a another try, gparted can't found my partitions, but I can mount them. Look at attached screenshot.

(At the screenshot gparted is started from System/Administration/GnomePartitionEditor but before I tried the dapper installer with the same result.

I want to install dapper without formating the whole disk. ](*,) 

(What I did at the first install was to format two ntfs partitions as reiserns. At the last step before installing the installer wanted to format the partitions to ext3. I then canseled and was trying again. This time I told the installer it was ok to format the two partitions as ext3 even though I wanted reiserns. The partioning started but nothing happend. I waited for 5 min but still it was at 0%. I then canceled again. Now I gave it a new try but now the installer can't find any of the partitions. I could have been trying to format a primary partition as reiser. I'm not really sure.)

```
 Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1        1530    12289693+  83  Linux
/dev/sda2            1531       21119   157348581+   f  W95 Ext'd (LBA)
/dev/sda3           21120       24792    29503372+  83  Linux
/dev/sda4               1           1           0+  83  Linux
Partition 4 does not end on cylinder boundary.
/dev/sda5           16829       19377    20474811    b  W95 FAT32
/dev/sda6           19378       19504     1020096   82  Linux swap / Solaris
/dev/sda7           19505       20450     7598713+  83  Linux
/dev/sda8           20451       20959     4088511   83  Linux
/dev/sda9           20960       21119     1285168+  83  Linux
/dev/sda10           1531       16828   122881122   83  Linux
/dev/sda11           1531        1531           0+  83  Linux

```

---

