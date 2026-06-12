---
title: "HW Raid 1 showing up as 4 different things"
date: 2012-09-16
forum: General Help
---

### Post by benwayj on 2012-09-16
I recently installed two identical harddrives and defined them in bios as a raid 1.  What's baffling me is that ubuntu lists these drives as sdc1, sdd1, /dev/mapper/pdc_bcacgaiie, and /dev/mapper/pdc_bcagaiie1.  Here is the fdisk -l printout for the relevent drives:

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1            2048  3906248703  1953123328   83  Linux

Disk /dev/sdd: 2000.4 GB, 2000398934016 bytes
255 heads, 63 sectors/track, 243201 cylinders, total 3907029168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disk identifier: 0x00070c9f

   Device Boot      Start         End      Blocks   Id  System
/dev/sdd1            2048  3906248703  1953123328   83  Linux

Disk /dev/mapper/pdc_bcacgaiie: 2000.0 GB, 1999999991808 bytes
255 heads, 63 sectors/track, 243152 cylinders, total 3906249984 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disk identifier: 0x00070c9f

                    Device Boot      Start         End      Blocks   Id  System
/dev/mapper/pdc_bcacgaiie1            2048  3906248703  1953123328   83  Linux

Disk /dev/mapper/pdc_bcacgaiie1: 2000.0 GB, 1999998287872 bytes
255 heads, 63 sectors/track, 243152 cylinders, total 3906246656 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disk identifier: 0x00000000

Disk /dev/mapper/pdc_bcacgaiie1 doesn't contain a valid partition table

My motherboard is this: [http://www.newegg.com/Product/Product.aspx?Item=N82E16813128510](http://www.newegg.com/Product/Product.aspx?Item=N82E16813128510)

What I'd like is to be able to understand what this is and what needs to be done to make my raid useable.

---

