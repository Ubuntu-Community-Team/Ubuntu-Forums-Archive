---
title: "Trying to mirror existing lvm"
date: 2009-11-23
forum: General Help
---

### Post by secundar on 2009-11-23
```
$ lvs -a -o +devices
  LV              VG    Attr   LSize   Origin Snap%  Move Log Copy%  Convert Devices                          
  root            aeria mwi-ao 100.00G                        100.00         root_mimage_0(0),root_mimage_1(0)
  [root_mimage_0] aeria iwi-ao 100.00G                                       /dev/sda1(0)                     
  [root_mimage_0] aeria iwi-ao 100.00G                                       /dev/sda1(19041)                 
  [root_mimage_1] aeria iwi-ao 100.00G                                       /dev/sdb1(0)                     
  root_mlog       aeria -wi-a-   4.00M                                       /dev/sdc1(0)                     
  swap_1          aeria -wi-ao   3.07G                                       /dev/sda1(18255)
```

Currently root is mirrored using ```
lvconvert -m1 --mirrolog core
```. This stores the mirror log to memory which is not ideal for a server environment. However, when using the default option of '--mirrolog disk' I receive an error:

```
lvconvert --mirrorlog disk aeria/root -vv
      Setting global/locking_type to 1
      File-based locking selected.
      Setting global/locking_dir to /var/lock/lvm
      Setting activation/mirror_region_size to 512
      Getting target version for mirror
      Getting target version for mirror
      Getting driver version
    Checking for existing volume group "aeria"
      Locking /var/lock/lvm/V_aeria WB
      /dev/ram0: No label detected
      /dev/loop0: size is 0 sectors
      /dev/sda: size is 312500000 sectors
      /dev/aeria/root: No label detected
      /dev/ram1: No label detected
      /dev/loop1: size is 0 sectors
      /dev/sda1: lvm2 label detected
      /dev/aeria/swap_1: No label detected
      /dev/ram2: No label detected
      /dev/loop2: size is 0 sectors
      /dev/sda2: size is 2 sectors
      /dev/aeria/root_mlog: No label detected
      /dev/ram3: No label detected
      /dev/loop3: size is 0 sectors
      /dev/mapper/aeria-root_mimage_0: No label detected
      /dev/ram4: No label detected
      /dev/loop4: size is 0 sectors
      /dev/mapper/aeria-root_mimage_1: No label detected
      /dev/ram5: No label detected
      /dev/loop5: size is 0 sectors
      /dev/sda5: No label detected
      /dev/ram6: No label detected
      /dev/loop6: size is 0 sectors
      /dev/ram7: No label detected
      /dev/loop7: size is 0 sectors
      /dev/ram8: No label detected
      /dev/ram9: No label detected
      /dev/ram10: No label detected
      /dev/ram11: No label detected
      /dev/ram12: No label detected
      /dev/ram13: No label detected
      /dev/ram14: No label detected
      /dev/ram15: No label detected
      /dev/sdb: size is 312581808 sectors
      /dev/sdb1: lvm2 label detected
      /dev/sdc: size is 2054144 sectors
      /dev/sdc1: lvm2 label detected
      Stack root:0[0] on LV root_mimage_0:0
      Adding root:0 as an user of root_mimage_0
      Stack root:0[1] on LV root_mimage_1:0
      Adding root:0 as an user of root_mimage_1
      Stack root:0[0] on LV root_mimage_0:0
      Adding root:0 as an user of root_mimage_0
      Stack root:0[1] on LV root_mimage_1:0
      Adding root:0 as an user of root_mimage_1
      Stack root:0[0] on LV root_mimage_0:0
      Adding root:0 as an user of root_mimage_0
      Stack root:0[1] on LV root_mimage_1:0
      Adding root:0 as an user of root_mimage_1
    Archiving volume group "aeria" metadata (seqno 9).
    Setting logging type to disk
      Setting activation/missing_stripe_filler to /dev/ioerror
      Setting activation/mirror_region_size to 512
    Creating logical volume root_mlog
      Locking LV yt2igPcEFEcM7xiVe8KakxMbRUUMPOKFLZiQTl21XiBBnlig87BaCZmDQiqvTFV8 (NL)
      Finding volume group for uuid yt2igPcEFEcM7xiVe8KakxMbRUUMPOKFLZiQTl21XiBBnlig87BaCZmDQiqvTFV8
      Stack root:0[0] on LV root_mimage_0:0
      Adding root:0 as an user of root_mimage_0
      Stack root:0[1] on LV root_mimage_1:0
      Adding root:0 as an user of root_mimage_1
      Stack root:0[0] on LV root_mimage_0:0
      Adding root:0 as an user of root_mimage_0
      Stack root:0[1] on LV root_mimage_1:0
      Adding root:0 as an user of root_mimage_1
      Stack root:0[0] on LV root_mimage_0:0
      Adding root:0 as an user of root_mimage_0
      Stack root:0[1] on LV root_mimage_1:0
      Adding root:0 as an user of root_mimage_1
    Found volume group "aeria"
      Can't find logical volume id yt2igPcEFEcM7xiVe8KakxMbRUUMPOKFLZiQTl21XiBBnlig87BaCZmDQiqvTFV8
  Failed to create mirror log.
      Unlocking /var/lock/lvm/V_aeria
```

I have three disks:

```
$ pvs
  PV         VG    Fmt  Attr PSize    PFree  
  /dev/sda1  aeria lvm2 a-    148.77G  45.70G
  /dev/sdb1  aeria lvm2 a-    149.05G  49.05G
  /dev/sdc1  aeria lvm2 a-   1000.00M 996.00M
```

sda is the new physical disk for the mirror data. sdc is a 1GB usb key for the mirror log.

I would prefer to solve this problem and use LVM mirror rather than raid1. This is a 64-bit Ubuntu 9.04 system.

---

### Post by secundar on 2009-11-27
bump!

---

