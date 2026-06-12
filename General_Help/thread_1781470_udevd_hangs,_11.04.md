---
title: "udevd hangs, 11.04"
date: 2011-06-13
forum: General Help
---

### Post by davea88 on 2011-06-13
Natty Narwhal, 11.04.  Suddenly on inserting a 4GByte thumb drive
I sometimes find it does not mount and 5-20% of cpu is going
to udevd.  

Rebooting fixes the problem for a while.
Here is some data from syslog recorded while
it was failing to mount the device in case that helps.

Jun 12 09:41:46 q2 kernel: [385661.508331] usb 2-1.4: new high speed USB device using ehci_hcd and address 35
Jun 12 09:41:46 q2 kernel: [385661.601441] scsi27 : usb-storage 2-1.4:1.0
Jun 12 09:41:47 q2 kernel: [385662.600621] scsi 27:0:0:0: Direct-Access     SanDisk  Cruzer           8.01 PQ: 0 ANSI: 0 CCS
Jun 12 09:41:47 q2 kernel: [385662.600993] scsi 27:0:0:1: CD-ROM            SanDisk  Cruzer           8.01 PQ: 0 ANSI: 0
Jun 12 09:41:47 q2 kernel: [385662.601565] sd 27:0:0:0: Attached scsi generic sg3 type 0
Jun 12 09:41:47 q2 kernel: [385662.604728] sd 27:0:0:0: [sdc] 7843839 512-byte logical blocks: (4.01 GB/3.73 GiB)
Jun 12 09:41:47 q2 kernel: [385662.605224] sd 27:0:0:0: [sdc] Write Protect is off
Jun 12 09:41:47 q2 kernel: [385662.605228] sd 27:0:0:0: [sdc] Mode Sense: 45 00 00 08
Jun 12 09:41:47 q2 kernel: [385662.605722] sd 27:0:0:0: [sdc] Asking for cache data failed
Jun 12 09:41:47 q2 kernel: [385662.605724] sd 27:0:0:0: [sdc] Assuming drive cache: write through
Jun 12 09:41:47 q2 kernel: [385662.609975] sr1: scsi3-mmc drive: 48x/48x tray
Jun 12 09:41:47 q2 kernel: [385662.610104] sr 27:0:0:1: Attached scsi CD-ROM sr1
Jun 12 09:41:47 q2 kernel: [385662.610193] sr 27:0:0:1: Attached scsi generic sg4 type 5
Jun 12 09:41:47 q2 kernel: [385662.610851] sd 27:0:0:0: [sdc] Asking for cache data failed
Jun 12 09:41:47 q2 kernel: [385662.610854] sd 27:0:0:0: [sdc] Assuming drive cache: write through
Jun 12 09:41:47 q2 kernel: [385662.611788]  sdc: sdc1
Jun 12 09:41:47 q2 kernel: [385662.614601] sd 27:0:0:0: [sdc] Asking for cache data failed
Jun 12 09:41:47 q2 kernel: [385662.614604] sd 27:0:0:0: [sdc] Assuming drive cache: write through
Jun 12 09:41:47 q2 kernel: [385662.614607] sd 27:0:0:0: [sdc] Attached SCSI removable disk
Jun 12 09:41:49 q2 kernel: [385664.354499] ISO 9660 Extensions: Microsoft Joliet Level 3
Jun 12 09:41:50 q2 kernel: [385664.865389] ISOFS: changing to secondary root
Jun 12 09:41:50 q2 kernel: [385664.870076] VFS: busy inodes on changed media or resized disk sr1
Jun 12 09:41:50 q2 kernel: [385665.003168] VFS: busy inodes on changed media or resized disk sr1
Jun 12 09:41:50 q2 kernel: [385665.028258] VFS: busy inodes on changed media or resized disk sr1
Jun 12 09:41:50 q2 kernel: [385665.042026] VFS: busy inodes on changed media or resized disk sr1

and the busy inodes just continues on till I reboot.


After reboot, I stick the same thumb drive in and the udev symbol
and the drive show up on my desktop and all is normal.

When I 'safely remove drive' both symbols go away. I remove drive.

Then I stick drive in again and the data is there. Fine.
'safely remove drive' again and the udev sticks around a few seconds
extra, but goes away. Seems ok

 ps -eaf |grep ude
root       387     1  0 10:22 ?        00:00:01 upstart-udev-bridge --daemon
root       392     1  0 10:22 ?        00:00:02 udevd --daemon
root      3867   392  0 10:42 ?        00:00:00 udevd --daemon
root      6468   392  0 10:42 ?        00:00:00 udevd --daemon


Just posting this in case it is of some interest to someone.

---

