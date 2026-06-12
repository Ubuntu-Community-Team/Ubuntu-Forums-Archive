---
title: "HDD Not Properly Mounted After Wake from Hibernate"
date: 2011-07-12
forum: General Help
---

### Post by stefanadelbert on 2011-07-12
I'm using Ubuntu on a PC with two HDD's (/dev/sda, /dev/sdb) as a fileserver. Some directories on the second HDD (/dev/sdb) are being shared via Samba.

/dev/sdb
-> /dev/sdb1 ext4
-> /dev/sdb2 ext4

If I suspend the machine and then wake it up using wakeonlan the second HDD (/dev/sdb2) appears to be mounted, but files on that drive are not accessible. If I unmount it and try to remount it I get problems.

I can replicate this like so

```

#everything working fine at this point
sudo stop smbd #just to make sure that samba is out of the way
sudo pm-suspend

```

I then send the machine WOL packet from another machine on the network and the fileserver wakes up. Then

```

sudo umount /dev/sbd1
sudo umount /dev/sbd2

```

But now the volumes/partitions on /dev/sdb2 seems to have disappeared!

```

stefan@fileserver:~$ sudo blkid
/dev/sda1: UUID="ace0e28d-6c27-427b-bc7b-3dd949efb3fd" TYPE="ext3" 
/dev/sda5: UUID="25c3807f-b7bb-44ec-843d-c4dc866117f0" TYPE="swap" 
/dev/sda6: UUID="a25f3cdf-4dd2-420b-81c2-fb49e12cddca" TYPE="ext3" 
stefan@fileserver:~$ sudo fdisk -l

Disk /dev/sda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x6133d131

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        2432    19535008+  83  Linux
/dev/sda2            2433       14593    97683232+   5  Extended
/dev/sda5            2433        2675     1951866   82  Linux swap / Solaris
/dev/sda6            2676       14593    95731303+  83  Linux

```

Here is an extract from lshw which shows that the HDD /dev/sdb itself is there, but the volumes/partitions on the drive are not evident:

```

        *-ide:1
             description: IDE interface
             product: 82801FR/FRW (ICH6R/ICH6RW) SATA Controller
             vendor: Intel Corporation
             physical id: 1f.2
             bus info: pci@0000:00:1f.2
             logical name: scsi2
             version: 04
             width: 32 bits
             clock: 66MHz
             capabilities: ide pm bus_master cap_list emulated
             configuration: driver=ata_piix latency=0
             resources: irq:20 ioport:fe00(size=8) ioport:fe10(size=4) ioport:fe20(size=8) ioport:fe30(size=4) ioport:fea0(size=16) memory:dff3bc00-dff3bfff
           *-disk
                description: SCSI Disk
                physical id: 0.1.0
                bus info: scsi@2:0.1.0
                logical name: /dev/sdb
                size: 465GiB (500GB)

```

When things are working properly lshw gives more information in the "*-disk" section, notably a different description and then also product, vendor, version, serial, etc. information.

Is it possible that after waking up, the drive is not being recognised correctly? Grasping at straws - udev? wrong module being loaded? incorrect driver being invoked?

---

### Post by stefanadelbert on 2011-07-13
--- delete content here as it was no longer relevant ---

---

