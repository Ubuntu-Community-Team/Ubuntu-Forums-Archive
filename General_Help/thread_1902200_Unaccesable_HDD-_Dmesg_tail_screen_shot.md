---
title: "Unaccesable HDD- Dmesg tail screen shot"
date: 2011-12-30
forum: General Help
---

### Post by addisor on 2011-12-30
I'm trying to recover data from a 80GB HDD and have taken it out of the XP machine and attached it using an IDE adaptor to the USB port. I'm beginning to think its beyond recovery. Can someone look at this dmesg please and advise?

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1        1016     3905473    c  W95 FAT32 (LBA)

Disk /dev/sdc: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xe366e366

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1               1        9729    78148161   83  Linux
root@ubuntu:~#  dmesg | tail
[ 1208.498202] EXT3-fs (sdc1): error loading journal
[ 1234.970564] EXT3-fs: barriers not enabled
[ 1256.559788] sd 7:0:0:0: [sdc] Unhandled sense code
[ 1256.559792] sd 7:0:0:0: [sdc]  Result: hostbyte=DID_ERROR driverbyte=DRIVER_SENSE
[ 1256.559798] sd 7:0:0:0: [sdc]  Sense Key : Hardware Error [current] 
[ 1256.559804] sd 7:0:0:0: [sdc]  Add. Sense: No additional sense information
[ 1256.559809] sd 7:0:0:0: [sdc] CDB: Read(10): 28 00 00 00 30 87 00 00 08 00
[ 1256.559822] end_request: I/O error, dev sdc, sector 12423
[ 1256.559858] JBD: IO error reading journal superblock
[ 1256.559864] EXT3-fs (sdc1): error loading journal
root@ubuntu:~#


I ran fsck and it worked, horrah

---

