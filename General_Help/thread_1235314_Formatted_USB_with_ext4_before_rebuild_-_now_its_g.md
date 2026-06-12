---
title: "Formatted USB with ext4 before rebuild - now its gone"
date: 2009-08-08
forum: General Help
---

### Post by BIACS on 2009-08-08
I have read posts on this but haven't stumbled on one that has helped me to resolve this. I had Ubuntu 9.04 installed on my Laptop but wanted to play around and try using the alternate CD to create a RAID0 with my internal SATA drives. I used two external USB drives to backup the data that was on those two internal drives before I wiped them with the alternate CD.

Being as I'm trying to make a complete break from Windows, I used GParted to delete the NTFS partitions on the two external USB drives. I then created new partitions and formatted them as ext4. Everything went fine and I was able to copy all the data over to those two external drives.

I am now back up and running with Ubuntu 9.04 again but when I plug those USB drives in they do not auto mount. Using sudo I have made a directory in /media and tried sudo mount /dev/sdc (and /sdd) /media/USB with a type of ext4 but I get the following error message:

craig@craig-laptop:/media$ sudo mount -t ext4 /dev/sdc /media/USB1/
mount: wrong fs type, bad option, bad superblock on /dev/sdc,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so


Here is my fdisk -l 

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x000e4ba7

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       60054   482383723+  83  Linux
/dev/sda2           60055       60801     6000277+   5  Extended
/dev/sda5           60055       60801     6000246   82  Linux swap / Solaris

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x0000ad2d

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       60801   488384001   83  Linux

Disk /dev/sdc: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x14e888bd

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1               1       60801   488384001   83  Linux

Disk /dev/sdd: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x5a200fa3

   Device Boot      Start         End      Blocks   Id  System
/dev/sdd1               1       60801   488384001   83  Linux

I tried to capture the dmesg | tail updates when I plugged the USB drives in. 

[ 1555.440179] sd 8:0:0:0: [sdd] Attached SCSI disk
[ 1555.440250] sd 8:0:0:0: Attached scsi generic sg4 type 0
[ 1555.458370] TKIP: RX tkey->key_idx=1 frame keyidx=2 priv=ffff880127caf540 (a lot of lines similar to this one)
[ 1550.017080] usb-storage: device found at 4
[ 1550.017082] usb-storage: waiting for device to settle before scanning
[ 1550.257593] usb 1-3: new high speed USB device using ehci_hcd and address 5
[ 1550.391757] usb 1-3: configuration #1 chosen from 1 choice
[ 1550.392433] scsi8 : SCSI emulation for USB Mass Storage devices
[ 1550.392952] usb-storage: device found at 5
[ 1550.392954] usb-storage: waiting for device to settle before scanning
[ 1549.869031] usb 1-4: new high speed USB device using ehci_hcd and address 4
[ 1550.014442] usb 1-4: configuration #1 chosen from 1 choice
[ 1550.016278] scsi7 : SCSI emulation for USB Mass Storage devices
[ 1550.017080] usb-storage: device found at 4
[ 1550.017082] usb-storage: waiting for device to settle before scanning
[ 1550.257593] usb 1-3: new high speed USB device using ehci_hcd and address 5
[ 1550.391757] usb 1-3: configuration #1 chosen from 1 choice
[ 1550.392433] scsi8 : SCSI emulation for USB Mass Storage devices
[ 1550.392952] usb-storage: device found at 5
[ 1550.392954] usb-storage: waiting for device to settle before scanning
[ 1555.395074] sd 8:0:0:0: [sdd] Mode Sense: 21 00 00 00
[ 1555.395076] sd 8:0:0:0: [sdd] Assuming drive cache: write through
[ 1555.395719] sd 8:0:0:0: [sdd] 976773168 512-byte hardware sectors: (500 GB/465 GiB)
[ 1555.396970] sd 8:0:0:0: [sdd] Write Protect is off
[ 1555.396972] sd 8:0:0:0: [sdd] Mode Sense: 21 00 00 00
[ 1555.396974] sd 8:0:0:0: [sdd] Assuming drive cache: write through
[ 1555.396976]  sdd: sdd1
[ 1555.440179] sd 8:0:0:0: [sdd] Attached SCSI disk
[ 1555.440250] sd 8:0:0:0: Attached scsi generic sg4 type 0
[ 1555.458370] TKIP: RX tkey->key_idx=1 frame keyidx=2 priv=ffff880127caf540
[ 1555.395074] sd 8:0:0:0: [sdd] Mode Sense: 21 00 00 00
[ 1555.395076] sd 8:0:0:0: [sdd] Assuming drive cache: write through
[ 1555.395719] sd 8:0:0:0: [sdd] 976773168 512-byte hardware sectors: (500 GB/465 GiB)
[ 1555.396970] sd 8:0:0:0: [sdd] Write Protect is off
[ 1555.396972] sd 8:0:0:0: [sdd] Mode Sense: 21 00 00 00
[ 1555.396974] sd 8:0:0:0: [sdd] Assuming drive cache: write through
[ 1555.396976]  sdd: sdd1
[ 1555.440179] sd 8:0:0:0: [sdd] Attached SCSI disk
[ 1555.440250] sd 8:0:0:0: Attached scsi generic sg4 type 0
[ 1555.458370] TKIP: RX tkey->key_idx=1 frame keyidx=2 priv=ffff880127caf540

When I view the drives in gparted the only option is to format. Just as an experiment I left the drives attached to the USB ports and booted with the Ubuntu installer CD to see if I could specify the mount points from there but they tried to force the format switch.

Any suggestions or posts that I missed.

---

### Post by BIACS on 2009-08-13
Apparently I was performing the wrong type of search for a solution. In case anyone else experiences similar, the solution was ridiculously simple. Run sudo fsck /dev/(the usb device) and allowed it to fix the blocks. It also kept prompting for permission to make repairs (3800+) so I just sat there with my finger on they Y key. Once that was done I was able to unplug the USB and have it auto mount when plugged back in.

---

### Post by Astrals on 2009-10-03
Thank you i have just spent about 2 hours looking for a simple fix for this. This checked my file system but i still have the issue of them not being available due to permissions.

---

