---
title: "Disks constantly remounting as read only"
date: 2010-06-11
forum: General Help
---

### Post by Fibonacci on 2010-06-11
Hello.

Just as the title says, my disks are constantly being remounted as read only. Even after I manually mount them and explicitly specify the rw option, after a while I find they have become read only.
Needless to say, working like that is impossible. Fortunately the root partition is not affected, but every other partition is.

How can I prevent that from happening?

---

### Post by HeirPixel on 2010-06-11
What type of discs are these? Are they partitions of one disc, individual HDDs, flash drives? A copy of your partition table would be quite helpful.

---

### Post by Fibonacci on 2010-06-11
> **HeirPixel said:**
> What type of discs are these?

SATA.

> **HeirPixel said:**
> Are they partitions of one disc, individual HDDs, flash drives?

Individual HDDs formatted as FAT32.

---

### Post by perham on 2010-06-11
post output of ```
sudo fdisk -l
sudo mount
cat /etc/fstab
dmesg | grep ata

```

---

### Post by Fibonacci on 2010-06-11
> **perham said:**
> post output of ```
sudo fdisk -l
sudo mount
cat /etc/fstab
dmesg | grep ata

```

```
$ sudo fdisk -l

Disk /dev/sda: 20.0 GB, 20020396032 bytes
16 heads, 63 sectors/track, 38792 cylinders
Units = cylinders of 1008 * 512 = 516096 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xe728e728

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       38559    19433704+   7  HPFS/NTFS

Disk /dev/sdc: 251.0 GB, 251000193024 bytes
255 heads, 63 sectors/track, 30515 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xe15f5781

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1               1       30515   245111706    c  W95 FAT32 (LBA)

Disk /dev/sdb: 82.0 GB, 81964302336 bytes
255 heads, 63 sectors/track, 9964 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x422701cf

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1        2486    19968763+  83  Linux
/dev/sdb2            2487        9963    60059002+   f  W95 Ext'd (LBA)
/dev/sdb5            2487        9963    60058971    b  W95 FAT32

$ sudo mount
/dev/sdb1 on / type ext3 (rw,relatime,errors=remount-ro)
proc on /proc type proc (rw)
none on /sys type sysfs (rw,noexec,nosuid,nodev)
none on /sys/fs/fuse/connections type fusectl (rw)
none on /sys/kernel/debug type debugfs (rw)
none on /sys/kernel/security type securityfs (rw)
none on /dev type devtmpfs (rw,mode=0755)
none on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=0620)
none on /dev/shm type tmpfs (rw,nosuid,nodev)
none on /var/run type tmpfs (rw,nosuid,mode=0755)
none on /var/lock type tmpfs (rw,noexec,nosuid,nodev)
none on /lib/init/rw type tmpfs (rw,nosuid,mode=0755)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/fibonacci/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=fibonacci)
/dev/sdb5 on /media/hdb5 type vfat (rw,nodev,uhelper=hal,uid=0,shortname=mixed,codepage=437,utf8,gid=46,flush,umask=003)
/dev/sda1 on /media/hda1 type fuseblk (rw,nosuid,nodev,allow_other,blksize=4096)
/dev/sdc1 on /media/sda1 type vfat (rw,nodev,uhelper=hal,uid=0,shortname=mixed,codepage=437,utf8,gid=46,flush,umask=003)

$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc                                       /proc           proc         defaults                                               0  0  
# /dev/sdb1
UUID=97448add-beea-44f5-9e0a-a4f1db4ded94  /               ext3         relatime,errors=remount-ro                             0  1  
/swapfile				   swap		   swap		defaults						0	0
/dev/scd1                                  /media/cdrom0   udf,iso9660  user,noauto,exec,utf8                                  0  0  
/dev/scd0                                  /media/cdrom1   udf,iso9660  user,noauto,exec,utf8                                  0  0  
/dev/fd0                                   /media/floppy0  auto         rw,user,noauto,exec,utf8                               0  0  
/dev/sdb5                                  /media/hdb5     vfat         uid=root,rw,nodev,uhelper=hal,shortname=mixed,codepage=437,utf8,gid=plugdev,flush,umask=003  0  0  
/dev/sdc1                                  /media/sda1     vfat         uid=root,rw,nodev,uhelper=hal,shortname=mixed,codepage=437,utf8,gid=plugdev,flush,umask=003                           0  0  
/dev/sda1                                  /media/hda1     ntfs         defaults                                               0  0  

$ dmesg | grep ata
[    0.000000]  BIOS-e820: 00000000ba730000 - 00000000ba740000 (ACPI data)
[    0.000000]  modified: 00000000ba730000 - 00000000ba740000 (ACPI data)
[    0.000000]   #0 [0000000000 - 0000001000]   BIOS data page ==> [0000000000 - 0000001000]
[    0.000000] Memory: 2997896k/3054780k available (4673k kernel code, 55632k reserved, 2121k data, 656k init, 2145476k highmem)
[    0.000000]       .data : 0xc0590663 - 0xc07a2e48   (2121 kB)
[    0.207288] libata version 3.00 loaded.
[    0.291171] ata_piix 0000:00:1f.1: version 2.13
[    0.291190] ata_piix 0000:00:1f.1: enabling device (0005 -> 0007)
[    0.291222] ata_piix 0000:00:1f.1: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[    0.291293] ata_piix 0000:00:1f.1: setting latency timer to 64
[    0.291496] scsi0 : ata_piix
[    0.291632] scsi1 : ata_piix
[    0.294612] ata1: PATA max UDMA/100 cmd 0x1f0 ctl 0x3f6 bmdma 0xffa0 irq 14
[    0.294618] ata2: PATA max UDMA/100 cmd 0x170 ctl 0x376 bmdma 0xffa8 irq 15
[    0.294667] ata_piix 0000:00:1f.2: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[    0.294676] ata_piix 0000:00:1f.2: MAP [ P0 -- P1 -- ]
[    0.294748] ata_piix 0000:00:1f.2: setting latency timer to 64
[    0.294816] scsi2 : ata_piix
[    0.294908] scsi3 : ata_piix
[    0.296454] ata3: SATA max UDMA/133 cmd 0xec00 ctl 0xe800 bmdma 0xdc00 irq 18
[    0.296459] ata4: SATA max UDMA/133 cmd 0xe400 ctl 0xe000 bmdma 0xdc08 irq 18
[    0.476017] ata1.00: ATAPI: HL-DT-ST DVDRAM GSA-4167B, DL10, max UDMA/33
[    0.476077] ata1.01: ATAPI: HL-DT-STDVD-ROM GDR8161B, 0100, max UDMA/33
[    0.492246] ata1.00: configured for UDMA/33
[    0.507717] ata1.01: configured for UDMA/33
[    0.536678] ata2.00: ATA-5: WDC WD200EB-11CPF0, 06.04G06, max UDMA/100
[    0.536684] ata2.00: 39102336 sectors, multi 16: LBA 
[    0.536910] ata2.01: ATA-7: Maxtor 6Y080L0, YAR41BW0, max UDMA/133
[    0.536915] ata2.01: 160086528 sectors, multi 16: LBA 
[    0.555835] ata2.00: configured for UDMA/100
[    0.555912] ata3.00: ATA-7: Maxtor 6L250S0, BACE1G10, max UDMA/133
[    0.555917] ata3.00: 490234752 sectors, multi 16: LBA48 NCQ (depth 0/32)
[    0.563931] ata2.01: configured for UDMA/100
[    0.572948] ata3.00: configured for UDMA/133
[    0.735125] Write protecting the kernel read-only data: 1840k
[    1.386081] EXT3-fs: mounted filesystem with ordered data mode.

```

Apparently the problem now affects one disk only - /dev/sdc. The others are working fine after remounting by hand.

---

### Post by perham on 2010-06-11
> **Fibonacci said:**
> ```

/dev/sdc1               1       30515   245111706    c  W95 FAT32 (LBA)


**[COLOR="Red"]/dev/sdc1 on /media/sda1 type vfat (rw,nodev,uhelper=hal,uid=0,shortname=mixed,codepage=437,utf8,gid=46,flush,umask=003)[/COLOR]**

/dev/sdc1                                  /media/sda1     vfat         uid=root,rw,nodev,uhelper=hal,shortname=mixed,codepage=437,utf8,gid=plugdev,flush,umask=003                           0  0  


```

Apparently the problem now affects one disk only - /dev/sdc. The others are working fine after remounting by hand.

there, sdc1 is also mounted as rw, so I don't really see where the problem is?

---

### Post by Fibonacci on 2010-06-11
> **perham said:**
> there, sdc1 is also mounted as rw, so I don't really see where the problem is?

Here:

> **Fibonacci said:**
> Just as the title says, **[COLOR="Red"]my disks are constantly being remounted as read only. Even after I manually mount them and explicitly specify the rw option, after a while I find they have become read only.[/COLOR]**

---

### Post by Fibonacci on 2010-06-11
Ran fsck on the affected disk and corrected some errors. It's not remounting now.

---

