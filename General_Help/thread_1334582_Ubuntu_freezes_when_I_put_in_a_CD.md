---
title: "Ubuntu freezes when I put in a CD"
date: 2009-11-22
forum: General Help
---

### Post by Bullfrog245 on 2009-11-22
I have recently installed Ubuntu 9.10 through Windows XP (I think this is called a WUBI install) Everything is working well for the most part, but whenever I try to put a CD or DVD into the computer, it will freeze (ie. the mouse stops moving, progress bars stop moving, everything just stops)

I have tried looking at the System > Administration > Disk Utility screen while I put the CD in the drive.  At first it shows my CD player (LIGHT-ON COMBO SOHC-5232K) at the location /dev/sr0 and says no media is detected.  I open the tray, put the CD in, and close the tray.  There is an area at the top of the screen that says something about mounting the CD with a spinning circle, then about 10 seconds later everything freezes.

If I try to click on the CD under Places, I get a message like:
DBus error org.gtk.Private.RemoteVolumeMonitor.Failed: An operation is already pending

I have two CD/DVD players (the other is a Sony) and both have the problem.  Both work in Windows fine.  I have tried unhooking each drive to see if there was a conflict, but the problem persists.  If I try to start Ubuntu with a CD already in the drive, it freezes a couple of seconds after I log in.

Anyone have any ideas?

---

### Post by ajgreeny on 2009-11-22
I have had this same problem once with just one single home recorded music CD which used to work OK without problem.  I have never sorted out the reason for this, but it was not a once only problem and affects both my desktop and my laptop machine, both running jaunty.  In both the machine locks solid and can only be rescued with a hard reboot.  I tried Ctrl+Alt+F1 etc to no avail, could not unfreeze it with the new equivalent of Ctrl+Alt+Backspace (AltGr+SysRq+K) and got nowhere with REISUB.

Does this sound the same as your problem, with the same lack of solution other than a hard reboot, and is it all CDs or just one or two that cause this problem?

---

### Post by Bullfrog245 on 2009-11-22
The symptoms are the same as you describe.  I have no way of recovering the system short of holding the power button until it turns off.

I have only tried three CD's/DVD's (mostly because I didn't want to restart my system too many times) but it has happened with all of them.  The disks were the first disk for Civilization IV, a disk that has the drivers for a HP Deskjet D1341 printer, and the DVD for Transformers.

---

### Post by Bullfrog245 on 2009-11-22
I don't know if this helps or not, but I looked at the syslog, and these this is what it says when I insert a CD.  I added the last line so that you could see that I waited 4 minutes before killing the power

```
Nov 22 20:54:06 ubuntu kernel: [   87.234403] cdrom: sr0: mrw address space DMA selected
Nov 22 20:54:06 ubuntu kernel: [   87.395410] sr 7:0:0:0: [sr0] Unhandled sense code
Nov 22 20:54:06 ubuntu kernel: [   87.395416] sr 7:0:0:0: [sr0] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
Nov 22 20:54:06 ubuntu kernel: [   87.395421] sr 7:0:0:0: [sr0] Sense Key : Hardware Error [current] 
Nov 22 20:54:06 ubuntu kernel: [   87.395428] sr 7:0:0:0: [sr0] Add. Sense: Logical unit communication CRC error (Ultra-DMA/32)
Nov 22 20:54:06 ubuntu kernel: [   87.395436] end_request: I/O error, dev sr0, sector 64
Nov 22 20:58:00 ubuntu kernel: imklog 4.2.0, log source = /var/run/rsyslog/kmsg started.
```


EDIT:

If I click on the CD through the places menu before the computer freezes, I get this error

DBus error org.gtk.Private.RemoteVolumeMonitor.Failed: An operation is already pending

---

### Post by gerar1995 on 2009-11-23
same problem here.
Also freezes with dvd's

---

### Post by dk75 on 2009-12-19
Actuall DVD's working for me, I have trouble with CDR only
```

dmesg |tail -n 100
[  481.334178]  [<ffffffff8106b149>] ? del_timer+0x59/0x70
[  481.334187]  [<ffffffff81527c85>] wait_for_common+0xd5/0x170
[  481.334195]  [<ffffffff81257e80>] ? elv_insert+0x140/0x1f0
[  481.334205]  [<ffffffff81053d60>] ? default_wake_function+0x0/0x10
[  481.334214]  [<ffffffff8125e76a>] ? __generic_unplug_device+0x1a/0x40
[  481.334223]  [<ffffffff81527db8>] wait_for_completion+0x18/0x20
[  481.334232]  [<ffffffff81265f77>] blk_execute_rq+0x87/0xe0
[  481.334243]  [<ffffffff81220675>] ? security_capable+0x25/0x30
[  481.334252]  [<ffffffff810690ae>] ? capable+0xe/0x50
[  481.334261]  [<ffffffff81269a75>] sg_io+0x285/0x3d0
[  481.334270]  [<ffffffff81390218>] ? media_changed+0x68/0xb0
[  481.334280]  [<ffffffff8126a465>] scsi_cmd_ioctl+0x4f5/0x550
[  481.334289]  [<ffffffff81529ccd>] ? unlock_kernel+0x2d/0x40
[  481.334298]  [<ffffffff8114ceb7>] ? __blkdev_get+0x167/0x3a0
[  481.334307]  [<ffffffff8139534c>] cdrom_ioctl+0x4c/0xab0
[  481.334315]  [<ffffffff8111d308>] ? __dentry_open+0x218/0x2e0
[  481.334324]  [<ffffffff810da539>] ? find_get_page+0x19/0xa0
[  481.334333]  [<ffffffff8134af7b>] sr_block_ioctl+0x5b/0xb0
[  481.334342]  [<ffffffff81267257>] __blkdev_driver_ioctl+0x67/0x80
[  481.334350]  [<ffffffff8126773d>] blkdev_ioctl+0x9d/0x630
[  481.334359]  [<ffffffff8114b757>] block_ioctl+0x37/0x40
[  481.334366]  [<ffffffff8112e36d>] vfs_ioctl+0x1d/0xa0
[  481.334375]  [<ffffffff812788aa>] ? __up_read+0x9a/0xc0
[  481.334383]  [<ffffffff8112e999>] do_vfs_ioctl+0x79/0x370
[  481.334393]  [<ffffffff8107cf29>] ? up_read+0x9/0x10
[  481.334401]  [<ffffffff8152c614>] ? do_page_fault+0x194/0x370
[  481.334409]  [<ffffffff8112ed11>] sys_ioctl+0x81/0xa0
[  481.334418]  [<ffffffff81012002>] system_call_fastpath+0x16/0x1b
[  481.334430] INFO: task devkit-disks-da:3107 blocked for more than 120 seconds.
[  481.334435] "echo 0 > /proc/sys/kernel/hung_task_timeout_secs" disables this message.
[  481.334440] devkit-disks- D 00000000ffffffff     0  3107   3106 0x00000000
[  481.334450]  ffff88009932fc28 0000000000000086 ffffffff811300b0 0000000000015880
[  481.334459]  ffff880099bdde70 0000000000015880 0000000000015880 0000000000015880
[  481.334469]  0000000000015880 ffff880099bdde70 0000000000015880 0000000000015880
[  481.334478] Call Trace:
[  481.334485]  [<ffffffff811300b0>] ? __pollwait+0x0/0xf0
[  481.334495]  [<ffffffff815286a7>] __mutex_lock_slowpath+0xd7/0x160
[  481.334504]  [<ffffffff8114d100>] ? blkdev_open+0x0/0xc0
[  481.334512]  [<ffffffff815285a6>] mutex_lock+0x26/0x50
[  481.334520]  [<ffffffff8114cd88>] __blkdev_get+0x38/0x3a0
[  481.334529]  [<ffffffff8114d100>] ? blkdev_open+0x0/0xc0
[  481.334537]  [<ffffffff8114d0fb>] blkdev_get+0xb/0x10
[  481.334544]  [<ffffffff8114d16c>] blkdev_open+0x6c/0xc0
[  481.334553]  [<ffffffff8111d1d6>] __dentry_open+0xe6/0x2e0
[  481.334562]  [<ffffffff8111d4d7>] nameidata_to_filp+0x57/0x70
[  481.334571]  [<ffffffff8112cb2a>] do_filp_open+0x2ca/0xac0
[  481.334580]  [<ffffffff811346cb>] ? iput+0x2b/0x70
[  481.334589]  [<ffffffff8113886b>] ? mntput_no_expire+0x2b/0x100
[  481.334598]  [<ffffffff8127ce32>] ? __strncpy_from_user+0x22/0x60
[  481.334606]  [<ffffffff811375a2>] ? alloc_fd+0x102/0x150
[  481.334615]  [<ffffffff8111cfa4>] do_sys_open+0x64/0x160
[  481.334624]  [<ffffffff8111d0cb>] sys_open+0x1b/0x20
[  481.334632]  [<ffffffff81012002>] system_call_fastpath+0x16/0x1b
[  481.334649] INFO: task mount:3381 blocked for more than 120 seconds.
[  481.334654] "echo 0 > /proc/sys/kernel/hung_task_timeout_secs" disables this message.
[  481.334660] mount         D 0000000000000000     0  3381   3378 0x00000000
[  481.334669]  ffff880098497738 0000000000000082 ffff8800984976c8 0000000000015880
[  481.334679]  ffff8800a930c7c0 0000000000015880 0000000000015880 0000000000015880
[  481.334688]  0000000000015880 ffff8800a930c7c0 0000000000015880 0000000000015880
[  481.334697] Call Trace:
[  481.334707]  [<ffffffff81527fd5>] schedule_timeout+0x1d5/0x230
[  481.334717]  [<ffffffff81036419>] ? default_spin_lock_flags+0x9/0x10
[  481.334726]  [<ffffffff81527c85>] wait_for_common+0xd5/0x170
[  481.334735]  [<ffffffff81053d60>] ? default_wake_function+0x0/0x10
[  481.334744]  [<ffffffff8125e77d>] ? __generic_unplug_device+0x2d/0x40
[  481.334753]  [<ffffffff81527db8>] wait_for_completion+0x18/0x20
[  481.334762]  [<ffffffff81265f77>] blk_execute_rq+0x87/0xe0
[  481.334771]  [<ffffffff8126102b>] ? blk_rq_bio_prep+0x2b/0xc0
[  481.334779]  [<ffffffff812659b3>] ? blk_rq_append_bio+0x23/0x60
[  481.334787]  [<ffffffff81265ac6>] ? blk_rq_map_kern+0xd6/0x150
[  481.334796]  [<ffffffff8133d1b7>] scsi_execute+0xf7/0x160
[  481.334804]  [<ffffffff8134c0db>] sr_do_ioctl+0xeb/0x310
[  481.334812]  [<ffffffff8134c8c1>] ? sr_read_tochdr+0x101/0x170
[  481.334820]  [<ffffffff8134c862>] sr_read_tochdr+0xa2/0x170
[  481.334829]  [<ffffffff8134ce00>] sr_audio_ioctl+0xe0/0xf0
[  481.334837]  [<ffffffff8134ac56>] ? sr_test_unit_ready+0x66/0xf0
[  481.334847]  [<ffffffff811bc14d>] ? ext4_find_entry+0x37d/0x4d0
[  481.334856]  [<ffffffff813906c8>] cdrom_count_tracks+0x58/0x1a0
[  481.334864]  [<ffffffff8134bf25>] ? sr_drive_status+0x35/0xe0
[  481.334873]  [<ffffffff81390c24>] open_for_data+0x124/0x410
[  481.334882]  [<ffffffff8139358c>] cdrom_open+0x5c/0x200
[  481.334890]  [<ffffffff81268109>] ? get_disk+0x49/0x80
[  481.334899]  [<ffffffff81274a6a>] ? kobject_get+0x1a/0x30
[  481.334907]  [<ffffffff8134b0d4>] sr_block_open+0x74/0xd0
[  481.334915]  [<ffffffff812748c7>] ? kobject_put+0x27/0x60
[  481.334923]  [<ffffffff8114d100>] ? blkdev_open+0x0/0xc0
[  481.334931]  [<ffffffff8114cf5e>] __blkdev_get+0x20e/0x3a0
[  481.334940]  [<ffffffff8114d100>] ? blkdev_open+0x0/0xc0
[  481.334948]  [<ffffffff8114d0fb>] blkdev_get+0xb/0x10
[  481.334956]  [<ffffffff8114d16c>] blkdev_open+0x6c/0xc0
[  481.334964]  [<ffffffff8111d1d6>] __dentry_open+0xe6/0x2e0
[  481.334973]  [<ffffffff8111d4d7>] nameidata_to_filp+0x57/0x70
[  481.334982]  [<ffffffff8112cb2a>] do_filp_open+0x2ca/0xac0
[  481.334991]  [<ffffffff810f4619>] ? __do_fault+0x419/0x4e0
[  481.335000]  [<ffffffff81036419>] ? default_spin_lock_flags+0x9/0x10
[  481.335009]  [<ffffffff8127ce32>] ? __strncpy_from_user+0x22/0x60
[  481.335018]  [<ffffffff811375a2>] ? alloc_fd+0x102/0x150
[  481.335027]  [<ffffffff8111cfa4>] do_sys_open+0x64/0x160
[  481.335035]  [<ffffffff8111d0cb>] sys_open+0x1b/0x20
[  481.335044]  [<ffffffff81012002>] system_call_fastpath+0x16/0x1b

```

---

