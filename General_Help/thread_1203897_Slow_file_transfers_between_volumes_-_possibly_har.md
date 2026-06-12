---
title: "Slow file transfers between volumes - possibly hardware related?"
date: 2009-07-03
forum: General Help
---

### Post by samborambo on 2009-07-03
Hi I've been having an issue with my mythtv media centre for quite some time. I have a 5 drive RAID5 array with LVM and a number of volumes for storing various media. I also have a separate system drive for swap and OS. File copying between the system drive and the array is very slow. Usually 2 - 5MB/s. Writing a large dummy file to a volume on the array using dd is an acceptable 80MB/s and reading a large random file from the system drive is at least 20MB/s.

sda, sdb, sdc, sde and sdf make up the RAID5 array. sdd is the system drive.

```
# ls -l /dev/disk/by-path/
total 0
lrwxrwxrwx 1 root root 10 2009-05-17 19:40 pci-0000:00:09.0-scsi-0:0:0:0 -> ../../scd0
lrwxrwxrwx 1 root root  9 2009-05-17 19:40 pci-0000:00:0a.0-scsi-0:0:0:0 -> ../../sda
lrwxrwxrwx 1 root root  9 2009-05-17 19:40 pci-0000:00:0a.0-scsi-1:0:0:0 -> ../../sdb
lrwxrwxrwx 1 root root  9 2009-05-17 19:40 pci-0000:00:0a.0-scsi-2:0:0:0 -> ../../sdc
lrwxrwxrwx 1 root root  9 2009-05-17 19:40 pci-0000:00:0a.0-scsi-3:0:0:0 -> ../../sdd
lrwxrwxrwx 1 root root 10 2009-05-17 19:40 pci-0000:00:0a.0-scsi-3:0:0:0-part1 -> ../../sdd1
lrwxrwxrwx 1 root root 10 2009-05-17 19:40 pci-0000:00:0a.0-scsi-3:0:0:0-part2 -> ../../sdd2
lrwxrwxrwx 1 root root  9 2009-05-17 19:40 pci-0000:03:00.0-scsi-0:0:0:0 -> ../../sde
lrwxrwxrwx 1 root root  9 2009-05-17 19:40 pci-0000:03:00.0-scsi-2:0:0:0 -> ../../sdf

lrwxrwxrwx 1 root root   9 2009-05-17 19:40 scsi-1ATA_ST3250824AS_4ND2DD28 -> ../../sdd
lrwxrwxrwx 1 root root  10 2009-05-17 19:40 scsi-1ATA_ST3250824AS_4ND2DD28-part1 -> ../../sdd1
lrwxrwxrwx 1 root root  10 2009-05-17 19:40 scsi-1ATA_ST3250824AS_4ND2DD28-part2 -> ../../sdd2
lrwxrwxrwx 1 root root   9 2009-05-17 19:40 scsi-1ATA_WDC_WD5000AACS-00G8B0_WD-WCAUF0776443 -> ../../sde
lrwxrwxrwx 1 root root   9 2009-05-17 19:40 scsi-1ATA_WDC_WD5000AACS-00G8B0_WD-WCAUF0980657 -> ../../sda
lrwxrwxrwx 1 root root   9 2009-05-17 19:40 scsi-1ATA_WDC_WD5000AACS-00ZUB0_WD-WCASU3047127 -> ../../sdb
lrwxrwxrwx 1 root root   9 2009-05-17 19:40 scsi-1ATA_WDC_WD5000AACS-00ZUB0_WD-WCASU3049316 -> ../../sdc
lrwxrwxrwx 1 root root   9 2009-05-17 19:40 scsi-1ATA_WDC_WD5000AAKS-00YGA0_WD-WCAS80709859 -> ../../sdf


```

As you can see sda, sdb, sdc and sdd are on the motherboard SATA controller:

```
00:0a.0 SATA controller: nVidia Corporation MCP65 AHCI Controller (rev a3)
```

sde and sdf are on a PCIe 2 port SATA card:

```
03:00.0 RAID bus controller: Silicon Image, Inc. SiI 3132 Serial ATA Raid II Controller (rev 01)
```

Has anyone else had a similar problem? Nothing turns up in dmesg. I'm thinking that this may be some kernel related problem.

```
Linux mediabox 2.6.27-9-generic #1 SMP Thu Nov 20 21:57:00 UTC 2008 i686 GNU/Linux

```

Cheers,

Sam.

---

### Post by samborambo on 2009-07-22
*bump*

---

### Post by samborambo on 2009-08-09
*bump*

---

### Post by samborambo on 2009-08-30
*bump*

---

### Post by credobyte on 2009-08-30
Have been discussed multiple times .. I barely can get 5Mb/s ( should be OS related .. Fedora allows me to transfer files @ 15+Mb/s ).

---

