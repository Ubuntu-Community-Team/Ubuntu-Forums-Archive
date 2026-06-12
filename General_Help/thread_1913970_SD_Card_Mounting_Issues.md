---
title: "SD Card Mounting Issues"
date: 2012-01-23
forum: General Help
---

### Post by alexkrycek on 2012-01-23
Specs
-----
OS: Ubuntu 10.10
PC: Eee PC 900
SD: Transcend 16 Gb SDHC (Class 10)
-----

Hello,

I'm having problems getting Ubuntu to properly recognize this SD card. I've formatted it as FAT32, NTFS, EXT3 and finally EXT4. Now I can manually mount it, although it will register as a disk, not an SD card, and after a very long wait. I've tried using GParted, but it hangs on "Scanning all devices".

When I first insert the card, running "tail -f /var/log/messages" gives me:

```

[13554.363517] sd 2:0:0:0: [sdc] 31512576 512-byte logical blocks: (16.1 GB/15.0 GiB)
[13554.365386]  sdc: sdc1
[13680.288085] udisks-daemon D 00000001     0  1521   1520 0x00000000
[13680.288096]  eda79b88 00000086 00000000 00000001 f6f56000 f6f57f44 c090c480 c090c480
[13680.288111]  398eee7a 00000c54 c090c480 c090c480 00000000 00000c54 00000000 c090c480
[13680.288125]  c090c480 ed8d8000 f6ce2454 eda79c48 7fffffff eda79c4c eda79bec c05f2025
[13680.288140] Call Trace:
[13680.288158]  [<c05f2025>] schedule_timeout+0x1a5/0x270
[13680.288169]  [<c035d9ad>] ? kobject_put+0x1d/0x50
[13680.288180]  [<c01338c8>] ? default_spin_lock_flags+0x8/0x10
[13680.288189]  [<c05f3898>] ? _raw_spin_lock_irq+0x18/0x20
[13680.288197]  [<c05f1cc6>] wait_for_common+0xa6/0x120
[13680.288207]  [<c014b590>] ? default_wake_function+0x0/0x20
[13680.288216]  [<c05f1e17>] wait_for_completion+0x17/0x20
[13680.288224]  [<c03501ea>] blk_execute_rq+0x7a/0xd0
[13680.288231]  [<c03500a0>] ? blk_end_sync_rq+0x0/0x30
[13680.288240]  [<c034c0e2>] ? get_request_wait+0x22/0x180
[13680.288248]  [<c034b6ef>] ? __freed_request+0x9f/0x120
[13680.288256]  [<c034b79f>] ? freed_request+0x2f/0x50
[13680.288264]  [<c034c6a3>] ? blk_get_request+0x63/0x80
[13680.288274]  [<c043ddec>] scsi_execute+0xcc/0x120
[13680.288282]  [<c043e00a>] scsi_execute_req+0x8a/0x140
[13680.288291]  [<c043e15d>] scsi_test_unit_ready+0x9d/0x1c0
[13680.288302]  [<c02179f1>] ? kmem_cache_alloc_notrace+0x91/0xb0
[13680.288311]  [<c0458549>] sd_media_changed+0x169/0x240
[13680.288319]  [<c035db12>] ? kobject_get+0x12/0x20
[13680.288329]  [<c024ded6>] check_disk_change+0x26/0x60
[13680.288336]  [<c0455cb5>] sd_open+0x85/0x1d0
[13680.288343]  [<c035d9ad>] ? kobject_put+0x1d/0x50
[13680.288350]  [<c0455c30>] ? sd_open+0x0/0x1d0
[13680.288358]  [<c024eee9>] __blkdev_get+0x209/0x380
[13680.288366]  [<c024f06f>] blkdev_get+0xf/0x20
[13680.288374]  [<c024f13b>] blkdev_open+0xbb/0x100
[13680.288384]  [<c02222f4>] __dentry_open+0xc4/0x280
[13680.288392]  [<c0222599>] nameidata_to_filp+0x59/0x70
[13680.288400]  [<c024f080>] ? blkdev_open+0x0/0x100
[13680.288409]  [<c022da6f>] finish_open+0xbf/0x1a0
[13680.288417]  [<c02367a1>] ? dput+0x91/0x130
[13680.288425]  [<c022ec16>] do_last+0x66/0x3a0
[13680.288433]  [<c023099d>] do_filp_open+0x19d/0x4c0
[13680.288444]  [<c0435185>] ? scsi_device_put+0x35/0x50
[13680.288454]  [<c0222085>] do_sys_open+0x55/0x150
[13680.288462]  [<c02221ee>] sys_open+0x2e/0x40
[13680.288473]  [<c01093df>] sysenter_do_call+0x12/0x28
[13734.394040] sd 2:0:0:0: [sdc] Unhandled sense code
[13734.394045] sd 2:0:0:0: [sdc] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[13734.394054] sd 2:0:0:0: [sdc] Sense Key : Hardware Error [current] 
[13734.394064] sd 2:0:0:0: [sdc] Add. Sense: Unrecovered read error
[13734.394075] sd 2:0:0:0: [sdc] CDB: Read(10): 28 00 01 e0 d7 f0 00 00 08 00

```

Now, I have an 8 Gb SD card that, when inserted, is properly mounted and brings up a window. I don't believe it's the 16 Gb hardware though, as the previous log suggests, since my Windows XP partition reads it just fine.

I would definitely appreciate any suggestions. Thanks!

---

### Post by sudodus on 2012-01-23
I have a Transcend 32 Gb SDHC (Class 10) that should be similar to your 16 GB flash card. It has one partition formatted to FAT32. I have no problems with it using a built-in Chieftec card reader running Ubuntu 10.04.

I suggest that you try some other Ubuntu version: 10.04, 11.04 or the presently newest released version 11.10. Try with a live session booted from a USB drive.

---

### Post by alexkrycek on 2012-01-23
Since my other SD card works, I'm sure it's a misconfiguration somewhere. I feel that trying a different os will only confirm that.

---

### Post by sudodus on 2012-01-24
Can you see the flash drive now with ***gparted***? In that case, try the menu item 'Device -- Create Partition Table'.

Otherwise try the same with ***fdisk***. However it is less intuitive, so read the manual carefully before doing anything with it. Also remember that nothing is changed until you ask it to write. You can quit without writing if you change your mind.
```
man fdisk
```

---

