---
title: "LVM2 - missing LV but PV and VG still there"
date: 2011-08-21
forum: General Help
---

### Post by auphil on 2011-08-21
Hello Everyone,

I'm looking for some help in recovering/recreating a Logical Volume over existing data that appears to be just fine.

Something happened to my volume group when migrating my VMware Ubuntu VM from one host to another. I had three members of this VG:

root (lv0, pv0)
swap (lv1, pv0)
data (lv2, pv1)

Of the three, I only care about data. Note that it was on a separate "physical" vmdk (disk).

The data on this disk appears fine. On a new VM, it is on /dev/sdb1. However, the LV is gone. Note:

(The new machine is called "status", the old machine is called "euclid")

> root@status:~# vgdisplay 
  --- Volume group ---
  VG Name               euclid
  System ID             
  Format                lvm2
  Metadata Areas        1
  Metadata Sequence No  13
  VG Access             read/write
  VG Status             resizable
  MAX LV                0
  Cur LV                0
  Open LV               0
  Max PV                0
  Cur PV                1
  Act PV                1
  VG Size               1.07 TiB
  PE Size               4.00 MiB
  Total PE              281598
  Alloc PE / Size       0 / 0   
  Free  PE / Size       281598 / 1.07 TiB
  VG UUID               glLIec-9sWi-yEAF-40kQ-gMmN-HMF7-pTIv4v
   
  --- Volume group ---
  VG Name               status
  System ID             
  Format                lvm2
  Metadata Areas        1
  Metadata Sequence No  3
  VG Access             read/write
  VG Status             resizable
  MAX LV                0
  Cur LV                2
  Open LV               2
  Max PV                0
  Cur PV                1
  Act PV                1
  VG Size               11.76 GiB
  PE Size               4.00 MiB
  Total PE              3010
  Alloc PE / Size       3003 / 11.73 GiB
  Free  PE / Size       7 / 28.00 MiB
  VG UUID               OfSvVH-Rnvi-6u5l-jFLN-hwhk-qaKj-32G6dT
   
root@status:~# lvdisplay 
  --- Logical volume ---
  LV Name                /dev/status/root
  VG Name                status
  LV UUID                1GUhIr-0p1i-1gEa-ck4A-ctDG-OVde-Hn0FCa
  LV Write Access        read/write
  LV Status              available
  # open                 1
  LV Size                11.19 GiB
  Current LE             2865
  Segments               1
  Allocation             inherit
  Read ahead sectors     auto
  - currently set to     256
  Block device           251:0
   
  --- Logical volume ---
  LV Name                /dev/status/swap_1
  VG Name                status
  LV UUID                ieLOIr-jf4N-WZCN-M88Q-57OR-kZJV-M08MFg
  LV Write Access        read/write
  LV Status              available
  # open                 1
  LV Size                552.00 MiB
  Current LE             138
  Segments               1
  Allocation             inherit
  Read ahead sectors     auto
  - currently set to     256
  Block device           251:1
   
root@status:~# pvdisplay 
  --- Physical volume ---
  PV Name               /dev/sdb1
  VG Name               euclid
  PV Size               1.07 TiB / not usable 405.50 KiB
  Allocatable           yes 
  PE Size               4.00 MiB
  Total PE              281598
  Free PE               281598
  Allocated PE          0
  PV UUID               LuJnry-3cW7-xcAO-2lLs-7Frc-TnC3-N31iMe
   
  --- Physical volume ---
  PV Name               /dev/sda5
  VG Name               status
  PV Size               11.76 GiB / not usable 2.00 MiB
  Allocatable           yes 
  PE Size               4.00 MiB
  Total PE              3010
  Free PE               7
  Allocated PE          3003
  PV UUID               5dekRY-XY2C-VtNw-knjY-8Qhd-KHxh-Pre80s
   
 root@status:~# pvck -v /dev/sdb1
    Scanning /dev/sdb1
  Found label on /dev/sdb1, sector 1, type=LVM2 001
  Found text metadata area: offset=4096, size=192512
    Found LVM2 metadata record at offset=15872, size=1024, offset2=0 size2=0
    Found LVM2 metadata record at offset=14848, size=1024, offset2=0 size2=0
    Found LVM2 metadata record at offset=13824, size=1024, offset2=0 size2=0
    Found LVM2 metadata record at offset=12288, size=1536, offset2=0 size2=0
    Found LVM2 metadata record at offset=10752, size=1536, offset2=0 size2=0
    Found LVM2 metadata record at offset=9216, size=1536, offset2=0 size2=0
    Found LVM2 metadata record at offset=7680, size=1536, offset2=0 size2=0
    Found LVM2 metadata record at offset=6144, size=1536, offset2=0 size2=0
root@status:~# 


So, the simple objective is: how can I bring /dev/sdb1 back to the party?

Thanks in advance for any pointers.

AUPhil

---

