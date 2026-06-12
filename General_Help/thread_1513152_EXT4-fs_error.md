---
title: "EXT4-fs error"
date: 2010-06-19
forum: General Help
---

### Post by grumpy.biatch on 2010-06-19
I tried to test 'testdisk' by deleting the hard disk and recovering by testdisk. Managed to recover Ubuntu, Windows 7 and Data but couldnt boot the system. I used windows 7 disk to repair its boot and it helped getting in windows. Ubuntu is still unaccessible, I can not mount the drive with live cd. 

I have attached boot info script output. 

Below please find dmesg output - 

ubuntu@ubuntu:~$ sudo  dmesg | tail
[   75.416465] lp0: using parport0 (interrupt-driven).
[   77.672014] eth0: no IPv6 routers present
[  147.504020] Clocksource tsc unstable (delta = -273335510 ns)
[  165.070532] [drm] nouveau 0000:00:0d.0: nouveau_channel_free: freeing fifo 1
[  166.401834] [drm] nouveau 0000:00:0d.0: Allocating FIFO number 1
[  166.402090] [drm] nouveau 0000:00:0d.0: nouveau_channel_alloc: initialised FIFO 1
[  518.059653] EXT4-fs error (device sda5): ext4_ext_find_extent: bad header/extent in inode #8: invalid magic - magic 7061, entries 25441, max 25960(0), depth 11570(0)
[  518.059892] jbd2_journal_bmap: journal block not found at offset 0 on sda5-8
[  518.059898] jbd2_journal_init_inode: Cannnot locate journal superblock
[  518.059907] EXT4-fs (sda5): Could not load journal inode

---

### Post by dcstar on 2010-06-19
> **grumpy.biatch said:**
> I tried to test 'testdisk' by deleting the hard disk and recovering by testdisk. Managed to recover Ubuntu, Windows 7 and Data but couldnt boot the system. I used windows 7 disk to repair its boot and it helped getting in windows. Ubuntu is still unaccessible, I can not mount the drive with live cd. 
.........

If something has changed the partition or has not recovered it exactly as it was previously, then you will have issues. Even using Windows to "repair" things may have stuffed up the Linux partition.

---

### Post by grumpy.biatch on 2010-06-19
> **dcstar said:**
> If something has changed the partition or has not recovered it exactly as it was previously, then you will have issues. Even using Windows to "repair" things may have stuffed up the Linux partition.


Hi,

I didnt use windows to repair Ubuntu partition, it is just not possible. I used Ubuntu System Rescue Disk for testdisk and wrote the partition table the way it was. This is my second time messing around with ext4 fs but have not had any luck with it at all.

---

### Post by grumpy.biatch on 2010-06-20
> **grumpy.biatch said:**
> Hi,

I didnt use windows to repair Ubuntu partition, it is just not possible. I used Ubuntu System Rescue Disk for testdisk and wrote the partition table the way it was. This is my second time messing around with ext4 fs but have not had any luck with it at all.

Had no luck so far. Reinstalling Buntu.:confused:

---

