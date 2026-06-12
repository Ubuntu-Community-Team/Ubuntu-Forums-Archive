---
title: "Cant chown my USB discs"
date: 2010-12-17
forum: General Help
---

### Post by ialvik on 2010-12-17
[B]I have 3 USB discs connected to my Ubuntu 10.10. But I cant change the permissions.
I would like them to mount in fstab, can anyone please help.. Bit of a newbie...

I'll post som info:[/B]

Disk /dev/sda: 40.0 GB, 40016019456 bytes
255 heads, 63 sectors/track, 4865 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000a074e

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        4660    37427200   83  Linux
/dev/sda2            4660        4865     1648641    5  Extended
/dev/sda5            4660        4865     1648640   82  Linux swap / Solaris

WARNING: GPT (GUID Partition Table) detected on '/dev/sdb'! The util fdisk doesn't support GPT. Use GNU Parted.


Disk /dev/sdb: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x25016f4f

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1          26      204819+  ee  GPT
/dev/sdb2              26      121602   976556032    7  HPFS/NTFS

Disk /dev/sdc: 1000.2 GB, 1000202043392 bytes
255 heads, 63 sectors/track, 121600 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x0002adcd

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1               1      121601   976758784    7  HPFS/NTFS

WARNING: GPT (GUID Partition Table) detected on '/dev/sdd'! The util fdisk doesn't support GPT. Use GNU Parted.


Disk /dev/sdd: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sdd1               1      121602   976762580   ee  GPT
[email]root@S51:/home/iver/.sickbe[/email]ard# lsusb
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 002: ID 045e:00f9 Microsoft Corp. Wireless Desktop Receiver 3.1
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 007: ID 1058:1003 Western Digital Technologies, Inc. 
Bus 001 Device 005: ID 1058:1021 Western Digital Technologies, Inc. 
Bus 001 Device 004: ID 05e3:0606 Genesys Logic, Inc. USB 2.0 Hub / D-Link DUB-H4 USB 2.0 Hub
Bus 001 Device 003: ID 059f:1019 LaCie, Ltd Desktop Hard Drive
Bus 001 Device 002: ID 04a9:10b6 Canon, Inc. PIXMA iP4300 Printer
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
[email]root@S51:/home/iver/.sickbe[/email]ard# dmesg | grep usb
[    0.374892] usbcore: registered new interface driver usbfs
[    0.374920] usbcore: registered new interface driver hub
[    0.374971] usbcore: registered new device driver usb
[    1.079828] usb 1-1: new high speed USB device using ehci_hcd and address 2
[    1.324040] usb 1-3: new high speed USB device using ehci_hcd and address 3
[    1.568035] usb 1-4: new high speed USB device using ehci_hcd and address 4
[    1.812029] usb 1-5: new high speed USB device using ehci_hcd and address 5
[    2.072365] usb 1-4.1: new high speed USB device using ehci_hcd and address 7
[    2.405043] usb 4-2: new low speed USB device using uhci_hcd and address 2
[   16.964612] usbcore: registered new interface driver hiddev
[   16.965903] usblp0: USB Bidirectional printer dev 2 if 0 alt 0 proto 2 vid 0x04A9 pid 0x10B6
[   16.966201] usbcore: registered new interface driver usbhid
[   16.966207] usbhid: USB HID core driver
[   16.967536] usbcore: registered new interface driver usblp
[   16.990460] scsi2 : usb-storage 1-3:1.0
[   17.014187] input: Microsft Microsoft Wireless Desktop Receiver 3.1 as /devices/pci0000:00/0000:00:1d.2/usb4/4-2/4-2:1.0/input/input2
[   17.014462] microsoft 0003:045E:00F9.0001: input,hidraw0: USB HID v1.11 Keyboard [Microsft Microsoft Wireless Desktop Receiver 3.1] on usb-0000:00:1d.2-2/input0
[   17.052030] scsi3 : usb-storage 1-5:1.0
[   17.099141] scsi4 : usb-storage 1-4.1:1.0
[   17.116756] usbcore: registered new interface driver usb-storage
[   17.157626] input: Microsft Microsoft Wireless Desktop Receiver 3.1 as /devices/pci0000:00/0000:00:1d.2/usb4/4-2/4-2:1.1/input/input3
[   17.157870] microsoft 0003:045E:00F9.0002: input,hidraw1: USB HID v1.11 Mouse [Microsft Microsoft Wireless Desktop Receiver 3.1] on usb-0000:00:1d.2-2/input1
[   20.674838] usb 1-1: usbfs: interface 0 claimed by usblp while 'usb' sets con

---

### Post by redmk2 on 2010-12-17
> **ialvik said:**
> [B]I have 3 USB discs connected to my Ubuntu 10.10. But I cant change the permissions.
I would like them to mount in fstab, can anyone please help.. Bit of a newbie...

I'll post som info:[/B]

```
Disk /dev/sda: 40.0 GB, 40016019456 bytes
255 heads, 63 sectors/track, 4865 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000a074e

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        4660    37427200   83  Linux
/dev/sda2            4660        4865     1648641    5  Extended
/dev/sda5            4660        4865     1648640   82  Linux swap / Solaris

WARNING: GPT (GUID Partition Table) detected on '/dev/sdb'! The util fdisk doesn't support GPT. Use GNU Parted.


Disk /dev/sdb: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x25016f4f

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1          26      204819+  ee  GPT
/dev/sdb2              26      121602   976556032    7  **[COLOR="Red"]HPFS/NTFS[/COLOR]**

Disk /dev/sdc: 1000.2 GB, 1000202043392 bytes
255 heads, 63 sectors/track, 121600 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x0002adcd

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1               1      121601   976758784    7  [COLOR="red"]HPFS/NTFS[/COLOR]

WARNING: GPT (GUID Partition Table) detected on '/dev/sdd'! The util fdisk doesn't support GPT. Use GNU Parted.


Disk /dev/sdd: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sdd1               1      121602   976762580   ee  GPT

```
...



It appears that 2 of these disks are formatted as NTFS (see red items above). NTFS does not support Linux style users/groups permissions (no chown or chmod).  However, you can declare ownership when mounting the mounting the partition.  See the following man pages ```
man mount 8
```

The *-o *switch (options) allows you to declare the UID/GUID of your choosing.

The last drive listed may not have a file system on it at all.

---

### Post by srs5694 on 2010-12-17
You can also specify mount options in the /etc/fstab file, as in:

```

/dev/sdb1    /mnt/shared    ntfs-3g    uid=1000,fmask=133        0 0

```

This example mounts /dev/sdb1 to /mnt/shared, setting file ownership to the user with a user ID (UID) value of 1000 (usually the first user on Ubuntu systems) and setting file permissions to rw-r--r-- (unless files are marked as read-only, in which case they'll be r--r--r--).

One other comment: Two of those disks (/dev/sdb and /dev/sdd) are [GUID Partition Table (GPT)](http://en.wikipedia.org/wiki/GUID_Partition_Table) disks with [hybrid MBRs.](http://www.rodsbooks.com/gdisk/hybrid.html) Linux will use the GPT side, so the fdisk output you've posted may not reflect the true partition numbers, type codes, or even the number of partitions on these disks. Use GNU parted, as the fdisk warning suggests, or [gdisk](http://www.rodsbooks.com/gdisk), to view or modify GPT partitions.

---

