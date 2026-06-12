---
title: "Mount Fakeraid"
date: 2011-01-11
forum: General Help
---

### Post by PoppinJ on 2011-01-11
I finally have my fakeraid set up but it will not show up unless i run gparted first. I cant find a way to mount the devices without running gparted. Once i run gparted the raid arrays will automatically show up everywhere (disk utility, places, computer ect) and are easy to mount, but before gparted maps them out they don't show up anywhere, its like they dont exist. Does anyone know how I can get them to show up after every reboot without running gparted every time?

fdisk -l

Disk /dev/sda: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00550055

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1          13      102400    7  HPFS/NTFS
Partition 1 does not end on cylinder boundary.
/dev/sda2              13       13131   105369600    7  HPFS/NTFS
/dev/sda3           13131       30402   138724353    5  Extended
/dev/sda5           13131       13496     2928640   82  Linux swap / Solaris
/dev/sda6           13496       13557      487424   83  Linux
/dev/sda7           13557       14773     9764864   83  Linux
/dev/sda8           14773       30402   125540352   83  Linux

WARNING: GPT (GUID Partition Table) detected on '/dev/sdb'! The util fdisk doesn't support GPT. Use GNU Parted.


Disk /dev/sdb: 2000.4 GB, 2000398934016 bytes
255 heads, 63 sectors/track, 243201 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1      243153  1953124991+  ee  GPT

WARNING: GPT (GUID Partition Table) detected on '/dev/sdc'! The util fdisk doesn't support GPT. Use GNU Parted.


Disk /dev/sdc: 2000.4 GB, 2000398934016 bytes
255 heads, 63 sectors/track, 243201 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1               1      243153  1953124991+  ee  GPT

WARNING: GPT (GUID Partition Table) detected on '/dev/sdd'! The util fdisk doesn't support GPT. Use GNU Parted.


Disk /dev/sdd: 2000.4 GB, 2000398934016 bytes
255 heads, 63 sectors/track, 243201 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sdd1               1      243153  1953124991+  ee  GPT

WARNING: GPT (GUID Partition Table) detected on '/dev/sde'! The util fdisk doesn't support GPT. Use GNU Parted.


Disk /dev/sde: 2000.4 GB, 2000398934016 bytes
255 heads, 63 sectors/track, 243201 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sde1               1      243153  1953124991+  ee  GPT

WARNING: GPT (GUID Partition Table) detected on '/dev/dm-0'! The util fdisk doesn't support GPT. Use GNU Parted.


Disk /dev/dm-0: 2000.0 GB, 1999999991808 bytes
255 heads, 63 sectors/track, 243152 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000

     Device Boot      Start         End      Blocks   Id  System
/dev/dm-0p1               1      243153  1953124991+  ee  GPT

WARNING: GPT (GUID Partition Table) detected on '/dev/dm-2'! The util fdisk doesn't support GPT. Use GNU Parted.


Disk /dev/dm-2: 2000.0 GB, 1999999991808 bytes
255 heads, 63 sectors/track, 243152 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000

     Device Boot      Start         End      Blocks   Id  System
/dev/dm-2p1               1      243153  1953124991+  ee  GPT

Disk /dev/dm-1: 2000.0 GB, 1999998287872 bytes
255 heads, 63 sectors/track, 243152 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x2052474d

This doesn't look like a partition table
Probably you selected the wrong device.

     Device Boot      Start         End      Blocks   Id  System
/dev/dm-1p1   ?         410      119791   958924038+  70  DiskSecure Multi-Boot
Partition 1 does not end on cylinder boundary.
/dev/dm-1p2   ?      121585      234786   909287957+  43  Unknown
Partition 2 does not end on cylinder boundary.
/dev/dm-1p3   ?       14052       14052           5   72  Unknown
Partition 3 does not end on cylinder boundary.
/dev/dm-1p4          164483      164486       25945    0  Empty
Partition 4 does not end on cylinder boundary.

Partition table entries are not in disk order

Disk /dev/dm-3: 2000.0 GB, 1999998287872 bytes
255 heads, 63 sectors/track, 243152 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x2052474d

This doesn't look like a partition table
Probably you selected the wrong device.

     Device Boot      Start         End      Blocks   Id  System
/dev/dm-3p1   ?         410      119791   958924038+  70  DiskSecure Multi-Boot
Partition 1 does not end on cylinder boundary.
/dev/dm-3p2   ?      121585      234786   909287957+  43  Unknown
Partition 2 does not end on cylinder boundary.
/dev/dm-3p3   ?       14052       14052           5   72  Unknown
Partition 3 does not end on cylinder boundary.
/dev/dm-3p4          164483      164486       25945    0  Empty
Partition 4 does not end on cylinder boundary.

Partition table entries are not in disk order




dmraid -ay

RAID set "pdc_bajfijdcge" already active
RAID set "pdc_bbfiheccii" already active


dmraid -r
                     [FONT=monospace]/dev/sdd: pdc, "pdc_bajfijdcge", mirror, ok, 3906249984 sectors, data@ 0
/dev/sdd: pdc, "pdc_bajfijdcge", mirror, ok, 3906249984 sectors, data@ 0
/dev/sdc: pdc, "pdc_bbfiheccii", mirror, ok, 3906249984 sectors, data@ 0
/dev/sdb: pdc, "pdc_bbfiheccii", mirror, ok, 3906249984 sectors, data@ 0[/FONT]

---

### Post by PoppinJ on 2011-01-11
I just ran dmraid -tay 
pdc_bajfijdcge: 0 3906249984 mirror core 2 131072 nosync 2 /dev/sdd 0 /dev/sde 0 1 handle_errors
pdc_bbfiheccii: 0 3906249984 mirror core 2 131072 nosync 2 /dev/sdb 0 /dev/sdc 0 1 handle_errors

whats a handle_error? Could that be the problem?

---

### Post by psusi on 2011-01-11
> **PoppinJ said:**
> I just ran dmraid -tay 
pdc_bajfijdcge: 0 3906249984 mirror core 2 131072 nosync 2 /dev/sdd 0 /dev/sde 0 1 handle_errors
pdc_bbfiheccii: 0 3906249984 mirror core 2 131072 nosync 2 /dev/sdb 0 /dev/sdc 0 1 handle_errors

whats a handle_error? Could that be the problem?

That is a flag telling the kernel that it should handle errors.

I'm confused by your question because gparted in the current Ubuntu release does not show dmraids at all in a default install.  The workaround is to install the kpartx package.  Did you do this?

Can you reboot (and don't run gparted ) and post the output of sudo blkid?

---

### Post by psusi on 2011-01-11
Wait, it just dawned on me.  What you aren't seeing is the PARTITIONS on the fakeraid until you run gparted.  That is because you are using the GPT partition table and dmraid doesn't understand that.

---

### Post by PoppinJ on 2011-01-11
Yes I installed kpartx. So if I reformat the drives with MBR then it should recognize the drives from now on?

---

### Post by psusi on 2011-01-12
Yes.

---

