---
title: "Cannot mount Logical Volume - Repair LVM"
date: 2012-02-16
forum: General Help
---

### Post by c.monty on 2012-02-16
Hi,

I'm searching for support in the area of LVM (Logical Volume Manager).

Since I accidently overwrote my partition table, I cannot mount any of the logical volumes. The complete story behind this is [here]("http://ubuntuforums.org/showthread.php?t=1918141").

The "original" disk partition layout is this:
Partition 1: ~150MB, boot
Partition 2: ~ 20GB, Windows XP
Partition 3: ~ 130GB, Linux with LUKS and LVM (rest of disk)

However, the output of fdisk -lu indicates issues with partition table:
```

Disk /dev/sda: 160.0 GB, 160040803840 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312579695 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1    *             63       321,299       321,237  83 Linux
/dev/sda2          42,283,080    42,299,144        16,065  83 Linux

```

According to this output, partition /dev/sda2 would have a size of ~8MB. This is certainly wrong.

I can open the LUKS device and display LVM configuration:
```

root@sysresccd /root % cryptsetup luksOpen /dev/sda2 sda2_crypt
Enter passphrase for /dev/sda2: 
root@sysresccd /root % vgscan --mknodes
  Reading all physical volumes.  This may take a while...
  Found volume group "vg" using metadata type lvm2
root@sysresccd /root % vgchange -a y
[COLOR="Red"]  device-mapper: resume ioctl failed: Invalid argument
  Unable to resume vg-swap (253:1)
  device-mapper: resume ioctl failed: Invalid argument
  Unable to resume vg-root (253:2)
  2 logical volume(s) in volume group "vg" now active[/COLOR]

root@sysresccd /root % pvdisplay 
  --- Physical volume ---
  PV Name               /dev/mapper/sda2_crypt
  VG Name               vg
  PV Size               128.88 GiB / not usable 1.31 MiB
  Allocatable           yes (but full)
  PE Size               4.00 MiB
  Total PE              32994
  Free PE               0
  Allocated PE          32994
  PV UUID               ibbTYj-WzS0-kwgj-rVMw-lBpT-12Bs-RO2adN
   
root@sysresccd /root % vgdisplay 
  --- Volume group ---
  VG Name               vg
  System ID             
  Format                lvm2
  Metadata Areas        1
  Metadata Sequence No  3
  VG Access             read/write
  VG Status             resizable
  MAX LV                0
  Cur LV                2
  Open LV               0
  Max PV                0
  Cur PV                1
  Act PV                1
  VG Size               128.88 GiB
  PE Size               4.00 MiB
  Total PE              32994
  Alloc PE / Size       32994 / 128.88 GiB
  Free  PE / Size       0 / 0   
  VG UUID               oUe0DS-dcGH-e6lg-holh-PjGJ-CM12-nrBD0n
   
root@sysresccd /root % lvdisplay 
  /dev/mapper/vg-swap: open failed: No such file or directory
  --- Logical volume ---
  LV Name                /dev/vg/swap
  VG Name                vg
  LV UUID                V3OlNR-ZlEM-7YWK-rgiy-nvAR-KGeF-CjqJa3
  LV Write Access        read/write
  LV Status              NOT available
  LV Size                2.54 GiB
  Current LE             650
  Segments               1
  Allocation             inherit
  Read ahead sectors     auto
   
  /dev/mapper/vg-root: open failed: No such file or directory
  --- Logical volume ---
  LV Name                /dev/vg/root
  VG Name                vg
  LV UUID                if0NAl-AvPe-0vlV-pive-99Se-fnsJ-H1rY1q
  LV Write Access        read/write
  LV Status              NOT available
  LV Size                126.34 GiB
  Current LE             32344
  Segments               1
  Allocation             inherit
  Read ahead sectors     auto

```

The output of dmesg confirms the failure in LVM:
```

[  591.258701] device-mapper: table: 253:1: dm-0 too small for target: start=2048, len=5324800, dev_size=11969
[  591.277617] device-mapper: table: 253:2: dm-0 too small for target: start=5326848, len=264962048, dev_size=11969

```

I strongly believe that all data is still on the disk.
Do you have any idea to fix the LVM issue?
Should I just add another PV and extend the volumge group "vg"?

THX

---

