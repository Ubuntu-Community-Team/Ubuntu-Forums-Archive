---
title: "2nd HDD not recognised"
date: 2011-02-28
forum: General Help
---

### Post by lpcstr on 2011-02-28
I'm using Mint 10 and I have two hard drives. One which contains both my Linux partition and my Windows 7 partition, and one which contains a single NTFS partition.

All partitions on sda are showing up correctly and are automatically mounted, but I can't mount the 2nd disk. **sdb shows up in /dev, but sdb1 does not.**

dmesg | grep sdb
```

[    2.298354] sd 3:0:0:0: [sdb] 312581808 512-byte logical blocks: (160 GB/149 GiB)
[    2.298648] sd 3:0:0:0: [sdb] Write Protect is off
[    2.298652] sd 3:0:0:0: [sdb] Mode Sense: 00 3a 00 00
[    2.298782] sd 3:0:0:0: [sdb] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    2.299355]  sdb: sdb1
[    2.307194] sd 3:0:0:0: [sdb] Attached SCSI disk

```lshw -C disk
```

  *-disk:0                
       description: ATA Disk
       product: WDC WD5001AALS-0
       vendor: Western Digital
       physical id: 0
       bus info: scsi@2:0.0.0
       logical name: /dev/sda
       version: 01.0
       serial: WD-WCASYC128292
       size: 465GiB (500GB)
       capabilities: partitioned partitioned:dos
       configuration: ansiversion=5 signature=7ac74741
  *-disk:1
       description: ATA Disk
       product: WDC WD1600AAJS-0
       vendor: Western Digital
       physical id: 1
       bus info: scsi@3:0.0.0
       logical name: /dev/sdb
       version: 01.0
       serial: WD-WCAV33631644
       size: 149GiB (160GB)
       capabilities: partitioned partitioned:dos
       configuration: ansiversion=5 signature=d9a4d61e
  *-cdrom
       description: DVD-RAM writer
       product: BDDVDRW GGC-H20L
       vendor: HL-DT-ST
       physical id: 0.0.0
       bus info: scsi@4:0.0.0
       logical name: /dev/cdrom
       logical name: /dev/cdrw
       logical name: /dev/dvd
       logical name: /dev/dvdrw
       logical name: /dev/scd0
       logical name: /dev/sr0
       version: 1.03
       capabilities: removable audio cd-r cd-rw dvd dvd-r dvd-ram
       configuration: ansiversion=5 status=nodisc

```fdisk /dev/sdb
```

Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       19458   156288000    7  HPFS/NTFS

```There is nothing about sdb in fstab. Anyone have any clue about what I should do?

---

### Post by seawolf167 on 2011-02-28
> **lpcstr said:**
> [B]sdb shows up in /dev, but sdb1 does not

[/B] ```

Device Boot      Start         End      Blocks   Id  System
**/dev/sdb1**               1       19458   156288000    7  HPFS/NTFS

```

Can you clarify this? It looks like sdb1 is showing up in /dev/sdb1?

Can you manually mount it?

```
sudo mkdir /media/somedrive
sudo mount /dev/sdb1 /media/somedrive
```

One thing you may want to do since this is an NTFS formatted drive is boot into Windows 7 and run [CHKDSK]("http://en.wikipedia.org/wiki/CHKDSK") on the drive to make sure all is ok with it.

Additionally, since it is a WD disk, you can download and run their [disk check tools]("http://support.wdc.com/product/download.asp?groupid=608&sid=3&lang=en") to ensure everything is preforming normally.

---

### Post by lpcstr on 2011-02-28
fdisk may show a "/dev/sdb1" but nautilus and ls both show that is doesn't exist.

In mountmanager it lists sdb with one partition also named sdb with a  file system of type isw_raid_member. I was using this disk in RAID at  one point before I started using it as a single disk. Windows 7 has no  problems accessing it.

---

### Post by Perfect Storm on 2011-03-01
Please use Mint forum, thanks.

You can find it here: [http://forums.linuxmint.com/](http://forums.linuxmint.com/)

---

