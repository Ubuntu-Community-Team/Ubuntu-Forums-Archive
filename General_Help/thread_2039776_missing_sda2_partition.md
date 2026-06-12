---
title: "missing sda2 partition"
date: 2012-08-09
forum: General Help
---

### Post by Austin Texas on 2012-08-09
Here is my situation:
I don't have any sda2.

```
dan@dan1:~$ ls -l /dev/disk/by-uuid/
total 0
lrwxrwxrwx 1 root root 10 Aug  9 08:59 0c2aa6cd-c125-402a-9cb1-e4177bdf7487 -> ../../sdb1
lrwxrwxrwx 1 root root 10 Aug  9 08:59 187973fa-9e2c-4401-b301-4683e00e27f1 -> ../../sda4
lrwxrwxrwx 1 root root 10 Aug  9 08:59 3e579c98-c280-47dd-b0b4-1960586b8b15 -> ../../sda3
lrwxrwxrwx 1 root root 10 Aug  9 08:59 5d27bacc-6643-435b-968b-c707b1bdd8f5 -> ../../sda1
lrwxrwxrwx 1 root root 10 Aug  9 08:59 82153a0f-bd07-450d-bd16-1939376f66f7 -> ../../sdb2
```

```
dan@dan1:~$ sudo blkid
[sudo] password for dan:
/dev/sda1: LABEL="first" UUID="5d27bacc-6643-435b-968b-c707b1bdd8f5" TYPE="ext4"
/dev/sda3: LABEL="third" UUID="3e579c98-c280-47dd-b0b4-1960586b8b15" SEC_TYPE="ext2" TYPE="ext3"
/dev/sda4: LABEL="swap" UUID="187973fa-9e2c-4401-b301-4683e00e27f1" TYPE="swap"
/dev/sdb1: LABEL="ubuntu" UUID="0c2aa6cd-c125-402a-9cb1-e4177bdf7487" TYPE="ext4"
/dev/sdb2: LABEL="backup" UUID="82153a0f-bd07-450d-bd16-1939376f66f7" TYPE="ext2"
```

as you can see, there is no sda2

I had an sda2. I used gparted to delete it, and then increased the size of sda1 to use the free space, because I needed a bigger sda1.
I did not use gparted to rebuild the partition tables. I didn't think it was necessary.
Now, even tho everything is working fine, I still feel like there is something wrong in the universe. I have 3 partitions, sda1, sda3 and sda4. There is a disturbance in the -force  and I have to fix it.
So the question is - would using gparted to rebuild the partition tables put my files on sda1 at risk?

sda1 - 330gigs, Linux Mint 13 MATE, all personal files
sda3 - 147gigs, test partition for various linux distros and kernels
sda4 - 8gigs swap
sdb1 - 10gigs, Ubuntu 12.04 LT, no personal files
sdb2 - 140gigs, backup of all personal files

hwinfo --block does not show sda2
```
dan@dan1:~$ hwinfo --block
> hal.1: read hal dataprocess 8171: arguments to dbus_move_error() were incorrect, assertion "(dest) == NULL || !dbus_error_is_set ((dest))" failed in file ../../dbus/dbus-errors.c line 282.
This is normally a bug in some application using the D-Bus library.
libhal.c 3483 : Error unsubscribing to signals, error=The name org.freedesktop.Hal was not provided by any .service files
39: IDE 00.0: 10600 Disk                                       
  [Created at block.243]
  Unique ID: 3OOL.7rkt_MqGvpD
  Parent ID: 7EWs.LJZ0nXV_p2E
  SysFS ID: /class/block/sda
  SysFS BusID: 0:0:0:0
  SysFS Device Link: /devices/pci0000:00/0000:00:11.0/host0/target0:0:0/0:0:0:0
  Hardware Class: disk
  Model: "ST3500418AS"
  Device: "ST3500418AS"
  Revision: "CC34"
  Driver: "ahci", "sd"
  Driver Modules: "ahci"
  Device File: /dev/sda
  Device Files: /dev/sda, /dev/disk/by-id/ata-ST3500418AS_6VM1VKQX, /dev/disk/by-id/scsi-SATA_ST3500418AS_6VM1VKQX, /dev/disk/by-id/wwn-0x5000c50013ffae52, /dev/disk/by-path/pci-0000:00:11.0-scsi-0:0:0:0
  Device Number: block 8:0-8:15
  BIOS id: 0x80
  Drive status: no medium
  Config Status: cfg=new, avail=yes, need=no, active=unknown
  Attached to: #12 (SATA controller)

40: None 00.0: 11300 Partition
  [Created at block.412]
  Unique ID: bdUI.SE1wIdpsiiC
  Parent ID: 3OOL.7rkt_MqGvpD
  SysFS ID: /class/block/sda/sda1
  Hardware Class: partition
  Model: "Partition"
  Device File: /dev/sda1
  Device Files: /dev/sda1, /dev/disk/by-id/ata-ST3500418AS_6VM1VKQX-part1, /dev/disk/by-id/scsi-SATA_ST3500418AS_6VM1VKQX-part1, /dev/disk/by-id/wwn-0x5000c50013ffae52-part1, /dev/disk/by-label/first, /dev/disk/by-path/pci-0000:00:11.0-scsi-0:0:0:0-part1, /dev/disk/by-uuid/5d27bacc-6643-435b-968b-c707b1bdd8f5
  Config Status: cfg=new, avail=yes, need=no, active=unknown
  Attached to: #39 (Disk)

41: None 00.0: 11300 Partition
  [Created at block.412]
  Unique ID: W__Q.SE1wIdpsiiC
  Parent ID: 3OOL.7rkt_MqGvpD
  SysFS ID: /class/block/sda/sda3
  Hardware Class: partition
  Model: "Partition"
  Device File: /dev/sda3
  Device Files: /dev/sda3, /dev/disk/by-id/ata-ST3500418AS_6VM1VKQX-part3, /dev/disk/by-id/scsi-SATA_ST3500418AS_6VM1VKQX-part3, /dev/disk/by-id/wwn-0x5000c50013ffae52-part3, /dev/disk/by-label/third, /dev/disk/by-path/pci-0000:00:11.0-scsi-0:0:0:0-part3, /dev/disk/by-uuid/3e579c98-c280-47dd-b0b4-1960586b8b15
  Config Status: cfg=new, avail=yes, need=no, active=unknown
  Attached to: #39 (Disk)

42: None 00.0: 11300 Partition
  [Created at block.412]
  Unique ID: z9FV.SE1wIdpsiiC
  Parent ID: 3OOL.7rkt_MqGvpD
  SysFS ID: /class/block/sda/sda4
  Hardware Class: partition
  Model: "Partition"
  Device File: /dev/sda4
  Device Files: /dev/sda4, /dev/disk/by-id/ata-ST3500418AS_6VM1VKQX-part4, /dev/disk/by-id/scsi-SATA_ST3500418AS_6VM1VKQX-part4, /dev/disk/by-id/wwn-0x5000c50013ffae52-part4, /dev/disk/by-label/swap, /dev/disk/by-path/pci-0000:00:11.0-scsi-0:0:0:0-part4, /dev/disk/by-uuid/187973fa-9e2c-4401-b301-4683e00e27f1
  Config Status: cfg=new, avail=yes, need=no, active=unknown
  Attached to: #39 (Disk)
```


gpart shows possible sda2:
```
dan@dan1:~$ sudo gpart /dev/sda
[sudo] password for dan:

Begin scan...
Possible partition(Linux swap), size(6228mb), offset(470709mb)
End scan.

Checking partitions...
Partition(Linux swap or Solaris/x86): primary
Ok.

Guessed primary partition table:
Primary partition(1)
   type: 130(0x82)(Linux swap or Solaris/x86)
   size: 6228mb #s(12755608) s(964012455-976768062)
   chs:  (1023/254/63)-(1023/254/63)d (60007/0/1)-(60800/254/61)r

Primary partition(2)
   type: 000(0x00)(unused)
   size: 0mb #s(0) s(0-0)
   chs:  (0/0/0)-(0/0/0)d (0/0/0)-(0/0/0)r

Primary partition(3)
   type: 000(0x00)(unused)
   size: 0mb #s(0) s(0-0)
   chs:  (0/0/0)-(0/0/0)d (0/0/0)-(0/0/0)r

Primary partition(4)
   type: 000(0x00)(unused)
   size: 0mb #s(0) s(0-0)
   chs:  (0/0/0)-(0/0/0)d (0/0/0)-(0/0/0)r
```

---

### Post by oldfred on 2012-08-09
A partition table has 4 blank entries. It only fills in data if you create a partition. And one can be the extended which really is a container for the logicals.

You do not have to have all four and you do not have to have them in order or the ones your have in order on the drive. You can reorder them, but that usually breaks things that are device specific.

Info on MBR
[http://www.dewassoc.com/kbase/hard_drives/master_boot_record.htm](http://www.dewassoc.com/kbase/hard_drives/master_boot_record.htm)
MBR details including 2TiB limit and GPT link
[http://en.wikipedia.org/wiki/Master_boot_record](http://en.wikipedia.org/wiki/Master_boot_record)

---

### Post by Austin Texas on 2012-08-09
Thanks, oldfred 
And while I was reviewing the problem I thought of what should have been an obvious solution to changing the numbers - just delete sda3 and sda4 and recreate them.  That worked.

---

### Post by oldfred on 2012-08-09
then you probably have to update the UUID in fstab for swap. 

fdisk has a command to reorder, but because it often breaks things, I do not often suggest it.

You can reorder the partition with fdisk:
sudo fdisk /dev/sda
x  # enter expert mode
f  # fix  partition table
r  # return
p  # to print
v  # to verify partition 
if ok
w  #  write the changes to disk

Reordering the partition table requires reinstall grub. And maybe changes to fstab.

---

### Post by Austin Texas on 2012-08-09
I changed the fstab in Ubuntu and Mint to the correct UUID.
I am glad you pointed that out.

---

