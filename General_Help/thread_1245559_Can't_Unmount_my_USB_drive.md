---
title: "Can't Unmount my USB drive"
date: 2009-08-20
forum: General Help
---

### Post by Stochastic on 2009-08-20
I'm having troubles unmounting my USB harddrive.  I know the disk is corrupting itself slowly, but I'd like to run an fsck on it to try to fix what I can, then grab as much data I can off it before it completely tanks.

Whenever I attempt to unmount it, the process hangs.

Here's the tail of dmesg when I plug it in:
```
[40299.796099] usb 1-2: new high speed USB device using ehci_hcd and address 3
[40299.929946] usb 1-2: configuration #1 chosen from 1 choice
[40299.944745] scsi3 : SCSI emulation for USB Mass Storage devices
[40299.950301] usb-storage: device found at 3
[40299.950309] usb-storage: waiting for device to settle before scanning
[40304.948305] usb-storage: device scan complete
[40304.948903] scsi 3:0:0:0: Direct-Access     WD       5000AAK External 1.06 PQ: 0 ANSI: 0
[40304.949341] sd 3:0:0:0: Attached scsi generic sg2 type 0
[40304.964762] sd 3:0:0:0: [sdb] 976773168 512-byte logical blocks: (500 GB/465 GiB)
[40304.965505] sd 3:0:0:0: [sdb] Write Protect is off
[40304.965509] sd 3:0:0:0: [sdb] Mode Sense: 00 00 00 00
[40304.965513] sd 3:0:0:0: [sdb] Assuming drive cache: write through
[40304.967005] sd 3:0:0:0: [sdb] Assuming drive cache: write through
[40304.967017]  sdb: sdb1 sdb2 sdb3
[40304.985137] sd 3:0:0:0: [sdb] Assuming drive cache: write through
[40304.985145] sd 3:0:0:0: [sdb] Attached SCSI disk
[40306.386117] kjournald starting.  Commit interval 5 seconds
[40306.386134] EXT3-fs warning: maximal mount count reached, running e2fsck is recommended
[40306.386817] EXT3 FS on sdb3, internal journal
[40306.386821] EXT3-fs: recovery complete.
[40306.386825] EXT3-fs: mounted filesystem with writeback data mode.
[40306.805050] kjournald starting.  Commit interval 5 seconds
[40306.805074] EXT3-fs warning: mounting fs with errors, running e2fsck is recommended
[40306.824798] EXT3 FS on sdb2, internal journal
[40306.824807] EXT3-fs: recovery complete.
[40306.824817] EXT3-fs: mounted filesystem with writeback data mode.
[40308.958724] EXT3-fs error (device sdb2): ext3_lookup: deleted inode referenced: 49296
[40309.009751] EXT3-fs error (device sdb2): ext3_lookup: deleted inode referenced: 49296
[40309.015880] EXT3-fs error (device sdb2): ext3_lookup: deleted inode referenced: 49296
[40309.048982] EXT3-fs error (device sdb2): ext3_lookup: deleted inode referenced: 49296
[40309.061253] EXT3-fs error (device sdb2): ext3_lookup: deleted inode referenced: 49296
[40309.065925] EXT3-fs error (device sdb2): ext3_lookup: deleted inode referenced: 49296
[40309.073909] EXT3-fs error (device sdb2): ext3_lookup: deleted inode referenced: 49296
[40309.075287] EXT3-fs error (device sdb2): ext3_lookup: deleted inode referenced: 49296
[40309.077489] EXT3-fs error (device sdb2): ext3_lookup: deleted inode referenced: 49296
[40309.078830] EXT3-fs error (device sdb2): ext3_lookup: deleted inode referenced: 49296
[40309.083591] EXT3-fs error (device sdb2): ext3_lookup: deleted inode referenced: 49296
[40309.094059] EXT3-fs error (device sdb2): ext3_lookup: deleted inode referenced: 49296
[40309.098459] EXT3-fs error (device sdb2): ext3_lookup: deleted inode referenced: 49296
[40309.099934] EXT3-fs error (device sdb2): ext3_lookup: deleted inode referenced: 49296
[40309.101703] EXT3-fs error (device sdb2): ext3_lookup: deleted inode referenced: 49296
[40309.102697] EXT3-fs error (device sdb2): ext3_lookup: deleted inode referenced: 49296
[40309.106768] EXT3-fs error (device sdb2): ext3_lookup: deleted inode referenced: 49296
[40309.107699] EXT3-fs error (device sdb2): ext3_lookup: deleted inode referenced: 49296
[40310.299032] EXT3-fs error (device sdb2): ext3_lookup: deleted inode referenced: 49296
[40313.276055] sd 3:0:0:0: [sdb] Sense Key : No Sense [current] 
[40313.276073] Info fld=0x0
[40313.276079] sd 3:0:0:0: [sdb] Add. Sense: No additional sense information
[40315.375192] sd 3:0:0:0: [sdb] Sense Key : No Sense [current] 
[40315.375209] Info fld=0x0
[40315.375215] sd 3:0:0:0: [sdb] Add. Sense: No additional sense information
[40319.163814] sd 3:0:0:0: [sdb] Sense Key : No Sense [current] 
[40319.163830] Info fld=0x0
[40319.163836] sd 3:0:0:0: [sdb] Add. Sense: No additional sense information
[40322.969238] sd 3:0:0:0: [sdb] Sense Key : No Sense [current] 
[40322.969256] Info fld=0x0
[40322.969261] sd 3:0:0:0: [sdb] Add. Sense: No additional sense information
[40326.684443] sd 3:0:0:0: [sdb] Sense Key : No Sense [current] 
[40326.684459] Info fld=0x0
[40326.684465] sd 3:0:0:0: [sdb] Add. Sense: No additional sense information
[40330.324937] sd 3:0:0:0: [sdb] Sense Key : No Sense [current] 
[40330.324954] Info fld=0x0
[40330.324960] sd 3:0:0:0: [sdb] Add. Sense: No additional sense information
[40332.274937] sd 3:0:0:0: [sdb] Sense Key : No Sense [current] 
[40332.274954] Info fld=0x0
[40332.274960] sd 3:0:0:0: [sdb] Add. Sense: No additional sense information
[40334.216826] sd 3:0:0:0: [sdb] Sense Key : No Sense [current] 
[40334.216842] Info fld=0x0
[40334.216848] sd 3:0:0:0: [sdb] Add. Sense: No additional sense information

```

Any ideas?

Is there a way to turn off Automounting of the USB drive so that I can run fsck on it?  Any ideas would be great.  Thanks.

---

### Post by Stochastic on 2009-08-20
AHA! I love fixing my own problems with a little research.

I added some lines to my /etc/fstab that included the mount options: noauto,rw,sync

and suddenly no more auto-mounting!

---

