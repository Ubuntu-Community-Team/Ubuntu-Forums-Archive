---
title: "Mounting 5tb Windows Stripe Raid"
date: 2010-12-30
forum: General Help
---

### Post by Zwan on 2010-12-30
Hi, making the move to Ubuntu entirely but I want to get my 5TB raid function.

I can't seem to get it to recognize.

fdisk -l:

```
Disk /dev/sdb: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000

Disk /dev/sdb doesn't contain a valid partition table

Disk /dev/sda: 1000.2 GB, 1000204886016 bytes
256 heads, 63 sectors/track, 121126 cylinders
Units = cylinders of 16128 * 512 = 8257536 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1      266306  2147483647+  ee  GPT

Disk /dev/sdc: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000

Disk /dev/sdc doesn't contain a valid partition table

Disk /dev/sdd: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000

Disk /dev/sdd doesn't contain a valid partition table

Disk /dev/sde: 300.1 GB, 300069052416 bytes
255 heads, 63 sectors/track, 36481 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000de439

   Device Boot      Start         End      Blocks   Id  System
/dev/sde1   *           1         487     3905536   82  Linux swap / Solaris
Partition 1 does not end on cylinder boundary.
/dev/sde2             487       36482   289127425    5  Extended
/dev/sde5             487       36482   289127424   83  Linux

Disk /dev/sdf: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000

Disk /dev/sdf doesn't contain a valid partition table

Disk /dev/dm-0: 5001.0 GB, 5001012183040 bytes
255 heads, 63 sectors/track, 608005 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 131072 bytes / 655360 bytes
Disk identifier: 0x00000000

Disk /dev/dm-0 doesn't contain a valid partition table
```

Any help? It works under windows? ( Its GPT I think btw)

Else I can re-partition and format it (its all backed up) but I want to be able to read the raid under windows as well...

---

### Post by Zwan on 2010-12-30
bump

---

### Post by Zwan on 2011-04-06
Bump again, its been a few months can I have some help please?

---

### Post by ronparent on 2011-04-06
Phew, that has been a long wait! 

Because you want to read your raid both with windows and Ubuntu you will have to use FakeRAID (I hate that designation). You didn't say which distribution you had installed (9.10, 10.04, 10.10 etc.). The ones I named all support raid natively (but with various quirks).

The support for the MB raid sets is a program called dmraid. It will be easy to determine if your MB raid chip set is supported. Just install it.

I must explain. Since your Ubuntu is not installed to a raid partition gparted, although in the install image, is not installed with the Ubuntu install and must be installed separately afterwards. Simply add it to your installed system - any method, synaptics, sortware center, sudo apt-get, etc. 

Once installed, if your system is supported, the raid partitions will be automatically activated and should show up in the file explorer (nautilus). 

Another possible issue is the size of the disk array. Windows should have automatically set up a GUID file system and although supported is linux may not readable is some circumstances by Ubuntu in a raid partition. If you have problems detecting or accessing your raid partitions after installing dmraid let us know.

---

### Post by psusi on 2011-04-06
Your fakeraid shows up in /dev/mapper.  Look in there and you should see something like foo_abdegea.  Normally there would also be numbered partitions, but there is currently a bug where GPT partitions are not recognized.  You can get them recognized by running sudo kpartx -a /dev/mapper/foo_whatever.

---

### Post by ronparent on 2011-04-06
+1

---

### Post by Zwany on 2011-04-07
Sorry forgot to mention, I'm on 10.10.

dmraid is already installed, tried "sudo kpartx -a /dev/mapper/isw_idjigaahd_5TB" as well which didn't do anything to my knowledge.

---

### Post by psusi on 2011-04-07
> **Zwany said:**
> Sorry forgot to mention, I'm on 10.10.

dmraid is already installed, tried "sudo kpartx -a /dev/mapper/isw_idjigaahd_5TB" as well which didn't do anything to my knowledge.

It should have created the partition devices.  You should now have isw_idjigaahd_5TB1, etc in /dev/mapper, and they should also show up on the places menu.

---

### Post by Zwan on 2011-04-08
> **psusi said:**
> It should have created the partition devices.  You should now have isw_idjigaahd_5TB1, etc in /dev/mapper, and they should also show up on the places menu.

well I tried to mount both /dev/mapper/isw... and /dev/dm-0 and it wont, the disk manager(on a windows machine atm so dont know what its called) says the partition is unknown.

Won't show up on places either.

Its an AMD motherboard using a SB850 chip

---

### Post by psusi on 2011-04-08
You have to mount the partition ( the one that ends in a digit ), not the whole disk.  After running kpartx, did the partition show up in /dev/mapper?

---

### Post by Zwany on 2011-04-10
no nothing turned up:
```

crw------- 1 root root 10, 59 2011-04-10 13:28 control
lrwxrwxrwx 1 root root      7 2011-04-10 13:28 isw_idjigaahd_5TB -> ../dm-1

```

Its just a backup drive, so I can re-format it if I want to, So what config will work under both linux and windows?

---

### Post by psusi on 2011-04-11
For it to work under both you need to use dmraid like you are.

Can you post the output of

```
sudo kpartx -l /dev/mapper/isw_idjigaahd_5TB
```

---

### Post by Zwan on 2011-04-13
It outputs nothing.

Even with the verbose option...


_[http://img684.imageshack.us/img684/9916/screenshotju.png](http://img684.imageshack.us/img684/9916/screenshotju.png)_

Uploaded with [ImageShack.us]("http://imageshack.us")

---

### Post by psusi on 2011-04-13
Hrm.. it looks like the array is not partitioned, or the partition table is corrupt.  What do you get when you run sudo parted /dev/mapper/isw_idjigaahd_5TB print?

---

### Post by Zwany on 2011-04-14
> **psusi said:**
> Hrm.. it looks like the array is not partitioned, or the partition table is corrupt.

How can it work while its corrupted???

```
Error: /dev/mapper/isw_idjigaahd_5TB: unrecognised disk label 
```

---

### Post by psusi on 2011-04-14
Are you sure Windows still recognizes partitions on that drive?  What does sudo fdisk -l /dev/mapper/isw_idjigaahd_5TB say?

---

### Post by Zwany on 2011-04-15
> **psusi said:**
> Are you sure Windows still recognizes partitions on that drive?  What does sudo fdisk -l /dev/mapper/isw_idjigaahd_5TB say?

Yes I'm super sure, it even pulled off 400gig just now. Check disk came up fine.

This is a linux bug.

```


Disk /dev/mapper/isw_idjigaahd_5TB: 5001.0 GB, 5001012183040 bytes
255 heads, 63 sectors/track, 608005 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 131072 bytes / 655360 bytes
Disk identifier: 0x00000000

Disk /dev/mapper/isw_idjigaahd_5TB doesn't contain a valid partition table
```

It just doesn't wanna see the partition.

---

### Post by psusi on 2011-04-15
Can you post the output of:

```
sudo dmraid -n /dev/sd?
```

---

### Post by Zwany on 2011-04-16
```
/dev/sdf: "pdc" and "isw" formats discovered (using isw)!
/dev/sdd: "pdc" and "isw" formats discovered (using isw)!
/dev/sdc: "pdc" and "isw" formats discovered (using isw)!
/dev/sdb: "pdc" and "isw" formats discovered (using isw)!
/dev/sda: "pdc" and "isw" formats discovered (using isw)!
/dev/sdf (isw):
0x000 sig: "  Intel Raid ISM Cfg Sig. 1.3.00"
0x020 check_sum: 3075215238
0x024 mpb_size: 636
0x028 family_num: 839860073
0x02c generation_num: 2222
0x030 error_log_size: 4080
0x034 attributes: 2684354561
0x038 num_disks: 5
0x039 num_raid_devs: 1
0x03a error_log_pos: 2
0x03c cache_size: 1899642679
0x040 orig_family_num: 839860073
0x044 power_cycle_count: 554091059
0x048 bbm_log_size: 0
0x0d8 disk[0].serial: "        9TE1BPDN"
0x0e8 disk[0].totalBlocks: 1953525168
0x0ec disk[0].scsiId: 0x70000
0x0f0 disk[0].status: 0x13a
0x0f4 disk[0].owner_cfg_num: 0x0
0x108 disk[1].serial: "        6TE09CNQ"
0x118 disk[1].totalBlocks: 1953525168
0x11c disk[1].scsiId: 0x20000
0x120 disk[1].status: 0x13a
0x124 disk[1].owner_cfg_num: 0x0
0x138 disk[2].serial: "        6TE095KM"
0x148 disk[2].totalBlocks: 1953525168
0x14c disk[2].scsiId: 0x30000
0x150 disk[2].status: 0x13a
0x154 disk[2].owner_cfg_num: 0x0
0x168 disk[3].serial: "        6TE0EYCK"
0x178 disk[3].totalBlocks: 1953525168
0x17c disk[3].scsiId: 0x40000
0x180 disk[3].status: 0x13a
0x184 disk[3].owner_cfg_num: 0x0
0x198 disk[4].serial: "        9TE162KC"
0x1a8 disk[4].totalBlocks: 1953525168
0x1ac disk[4].scsiId: 0x50000
0x1b0 disk[4].status: 0x13a
0x1b4 disk[4].owner_cfg_num: 0x0
0x1c8 isw_dev[0].volume: "             5TB"
0x1dc isw_dev[0].SizeHigh: 2
0x1d8 isw_dev[0].SizeLow: 1177665536
0x1e0 isw_dev[0].status: 0xc
0x1e4 isw_dev[0].reserved_blocks: 0
0x1e8 isw_dev[0].migr_priority: 0
0x1e9 isw_dev[0].num_sub_vol: 0
0x1ea isw_dev[0].tid: 1
0x1eb isw_dev[0].cng_master_disk: 0
0x1ec isw_dev[0].cache_policy: 0
0x1ee isw_dev[0].cng_state: 0
0x1ef isw_dev[0].cng_sub_state: 0
0x218 isw_dev[0].vol.curr_migr_unit: 0
0x21c isw_dev[0].vol.check_point_id: 0
0x220 isw_dev[0].vol.migr_state: 0
0x221 isw_dev[0].vol.migr_type: 0
0x222 isw_dev[0].vol.dirty: 0
0x223 isw_dev[0].vol.fs_state: 255
0x224 isw_dev[0].vol.verify_errors: 0
0x226 isw_dev[0].vol.verify_bad_blocks: 0
0x238 isw_dev[0].vol.map[0].pba_of_lba0: 0
0x23c isw_dev[0].vol.map[0].blocks_per_member: 1953520392
0x240 isw_dev[0].vol.map[0].num_data_stripes: 7630938
0x244 isw_dev[0].vol.map[0].blocks_per_strip: 256
0x246 isw_dev[0].vol.map[0].map_state: 0
0x247 isw_dev[0].vol.map[0].raid_level: 0
0x248 isw_dev[0].vol.map[0].num_members: 5
0x249 isw_dev[0].vol.map[0].num_domains: 1
0x24a isw_dev[0].vol.map[0].failed_disk_num: 255
0x24b isw_dev[0].vol.map[0].ddf: 1
0x268 isw_dev[0].vol.map[0].disk_ord_tbl[0]: 0x0
0x26c isw_dev[0].vol.map[0].disk_ord_tbl[1]: 0x1
0x270 isw_dev[0].vol.map[0].disk_ord_tbl[2]: 0x2
0x274 isw_dev[0].vol.map[0].disk_ord_tbl[3]: 0x3
0x278 isw_dev[0].vol.map[0].disk_ord_tbl[4]: 0x4

/dev/sdd (isw):
0x000 sig: "  Intel Raid ISM Cfg Sig. 1.3.00"
0x020 check_sum: 3075215238
0x024 mpb_size: 636
0x028 family_num: 839860073
0x02c generation_num: 2222
0x030 error_log_size: 4080
0x034 attributes: 2684354561
0x038 num_disks: 5
0x039 num_raid_devs: 1
0x03a error_log_pos: 2
0x03c cache_size: 1899642679
0x040 orig_family_num: 839860073
0x044 power_cycle_count: 554091059
0x048 bbm_log_size: 0
0x0d8 disk[0].serial: "        9TE1BPDN"
0x0e8 disk[0].totalBlocks: 1953525168
0x0ec disk[0].scsiId: 0x10000
0x0f0 disk[0].status: 0x13a
0x0f4 disk[0].owner_cfg_num: 0x0
0x108 disk[1].serial: "        6TE09CNQ"
0x118 disk[1].totalBlocks: 1953525168
0x11c disk[1].scsiId: 0x50000
0x120 disk[1].status: 0x13a
0x124 disk[1].owner_cfg_num: 0x0
0x138 disk[2].serial: "        6TE095KM"
0x148 disk[2].totalBlocks: 1953525168
0x14c disk[2].scsiId: 0x30000
0x150 disk[2].status: 0x13a
0x154 disk[2].owner_cfg_num: 0x0
0x168 disk[3].serial: "        6TE0EYCK"
0x178 disk[3].totalBlocks: 1953525168
0x17c disk[3].scsiId: 0x40000
0x180 disk[3].status: 0x13a
0x184 disk[3].owner_cfg_num: 0x0
0x198 disk[4].serial: "        9TE162KC"
0x1a8 disk[4].totalBlocks: 1953525168
0x1ac disk[4].scsiId: 0x50000
0x1b0 disk[4].status: 0x13a
0x1b4 disk[4].owner_cfg_num: 0x0
0x1c8 isw_dev[0].volume: "             5TB"
0x1dc isw_dev[0].SizeHigh: 2
0x1d8 isw_dev[0].SizeLow: 1177665536
0x1e0 isw_dev[0].status: 0xc
0x1e4 isw_dev[0].reserved_blocks: 0
0x1e8 isw_dev[0].migr_priority: 0
0x1e9 isw_dev[0].num_sub_vol: 0
0x1ea isw_dev[0].tid: 1
0x1eb isw_dev[0].cng_master_disk: 0
0x1ec isw_dev[0].cache_policy: 0
0x1ee isw_dev[0].cng_state: 0
0x1ef isw_dev[0].cng_sub_state: 0
0x218 isw_dev[0].vol.curr_migr_unit: 0
0x21c isw_dev[0].vol.check_point_id: 0
0x220 isw_dev[0].vol.migr_state: 0
0x221 isw_dev[0].vol.migr_type: 0
0x222 isw_dev[0].vol.dirty: 0
0x223 isw_dev[0].vol.fs_state: 255
0x224 isw_dev[0].vol.verify_errors: 0
0x226 isw_dev[0].vol.verify_bad_blocks: 0
0x238 isw_dev[0].vol.map[0].pba_of_lba0: 0
0x23c isw_dev[0].vol.map[0].blocks_per_member: 1953520392
0x240 isw_dev[0].vol.map[0].num_data_stripes: 7630938
0x244 isw_dev[0].vol.map[0].blocks_per_strip: 256
0x246 isw_dev[0].vol.map[0].map_state: 0
0x247 isw_dev[0].vol.map[0].raid_level: 0
0x248 isw_dev[0].vol.map[0].num_members: 5
0x249 isw_dev[0].vol.map[0].num_domains: 1
0x24a isw_dev[0].vol.map[0].failed_disk_num: 255
0x24b isw_dev[0].vol.map[0].ddf: 1
0x268 isw_dev[0].vol.map[0].disk_ord_tbl[0]: 0x0
0x26c isw_dev[0].vol.map[0].disk_ord_tbl[1]: 0x1
0x270 isw_dev[0].vol.map[0].disk_ord_tbl[2]: 0x2
0x274 isw_dev[0].vol.map[0].disk_ord_tbl[3]: 0x3
0x278 isw_dev[0].vol.map[0].disk_ord_tbl[4]: 0x4

/dev/sdc (isw):
0x000 sig: "  Intel Raid ISM Cfg Sig. 1.3.00"
0x020 check_sum: 3075215238
0x024 mpb_size: 636
0x028 family_num: 839860073
0x02c generation_num: 2222
0x030 error_log_size: 4080
0x034 attributes: 2684354561
0x038 num_disks: 5
0x039 num_raid_devs: 1
0x03a error_log_pos: 2
0x03c cache_size: 1899642679
0x040 orig_family_num: 839860073
0x044 power_cycle_count: 554091059
0x048 bbm_log_size: 0
0x0d8 disk[0].serial: "        9TE1BPDN"
0x0e8 disk[0].totalBlocks: 1953525168
0x0ec disk[0].scsiId: 0x10000
0x0f0 disk[0].status: 0x13a
0x0f4 disk[0].owner_cfg_num: 0x0
0x108 disk[1].serial: "        6TE09CNQ"
0x118 disk[1].totalBlocks: 1953525168
0x11c disk[1].scsiId: 0x20000
0x120 disk[1].status: 0x13a
0x124 disk[1].owner_cfg_num: 0x0
0x138 disk[2].serial: "        6TE095KM"
0x148 disk[2].totalBlocks: 1953525168
0x14c disk[2].scsiId: 0x40000
0x150 disk[2].status: 0x13a
0x154 disk[2].owner_cfg_num: 0x0
0x168 disk[3].serial: "        6TE0EYCK"
0x178 disk[3].totalBlocks: 1953525168
0x17c disk[3].scsiId: 0x40000
0x180 disk[3].status: 0x13a
0x184 disk[3].owner_cfg_num: 0x0
0x198 disk[4].serial: "        9TE162KC"
0x1a8 disk[4].totalBlocks: 1953525168
0x1ac disk[4].scsiId: 0x50000
0x1b0 disk[4].status: 0x13a
0x1b4 disk[4].owner_cfg_num: 0x0
0x1c8 isw_dev[0].volume: "             5TB"
0x1dc isw_dev[0].SizeHigh: 2
0x1d8 isw_dev[0].SizeLow: 1177665536
0x1e0 isw_dev[0].status: 0xc
0x1e4 isw_dev[0].reserved_blocks: 0
0x1e8 isw_dev[0].migr_priority: 0
0x1e9 isw_dev[0].num_sub_vol: 0
0x1ea isw_dev[0].tid: 1
0x1eb isw_dev[0].cng_master_disk: 0
0x1ec isw_dev[0].cache_policy: 0
0x1ee isw_dev[0].cng_state: 0
0x1ef isw_dev[0].cng_sub_state: 0
0x218 isw_dev[0].vol.curr_migr_unit: 0
0x21c isw_dev[0].vol.check_point_id: 0
0x220 isw_dev[0].vol.migr_state: 0
0x221 isw_dev[0].vol.migr_type: 0
0x222 isw_dev[0].vol.dirty: 0
0x223 isw_dev[0].vol.fs_state: 255
0x224 isw_dev[0].vol.verify_errors: 0
0x226 isw_dev[0].vol.verify_bad_blocks: 0
0x238 isw_dev[0].vol.map[0].pba_of_lba0: 0
0x23c isw_dev[0].vol.map[0].blocks_per_member: 1953520392
0x240 isw_dev[0].vol.map[0].num_data_stripes: 7630938
0x244 isw_dev[0].vol.map[0].blocks_per_strip: 256
0x246 isw_dev[0].vol.map[0].map_state: 0
0x247 isw_dev[0].vol.map[0].raid_level: 0
0x248 isw_dev[0].vol.map[0].num_members: 5
0x249 isw_dev[0].vol.map[0].num_domains: 1
0x24a isw_dev[0].vol.map[0].failed_disk_num: 255
0x24b isw_dev[0].vol.map[0].ddf: 1
0x268 isw_dev[0].vol.map[0].disk_ord_tbl[0]: 0x0
0x26c isw_dev[0].vol.map[0].disk_ord_tbl[1]: 0x1
0x270 isw_dev[0].vol.map[0].disk_ord_tbl[2]: 0x2
0x274 isw_dev[0].vol.map[0].disk_ord_tbl[3]: 0x3
0x278 isw_dev[0].vol.map[0].disk_ord_tbl[4]: 0x4

/dev/sdb (isw):
0x000 sig: "  Intel Raid ISM Cfg Sig. 1.3.00"
0x020 check_sum: 3075215238
0x024 mpb_size: 636
0x028 family_num: 839860073
0x02c generation_num: 2222
0x030 error_log_size: 4080
0x034 attributes: 2684354561
0x038 num_disks: 5
0x039 num_raid_devs: 1
0x03a error_log_pos: 2
0x03c cache_size: 1899642679
0x040 orig_family_num: 839860073
0x044 power_cycle_count: 554091059
0x048 bbm_log_size: 0
0x0d8 disk[0].serial: "        9TE1BPDN"
0x0e8 disk[0].totalBlocks: 1953525168
0x0ec disk[0].scsiId: 0x10000
0x0f0 disk[0].status: 0x13a
0x0f4 disk[0].owner_cfg_num: 0x0
0x108 disk[1].serial: "        6TE09CNQ"
0x118 disk[1].totalBlocks: 1953525168
0x11c disk[1].scsiId: 0x20000
0x120 disk[1].status: 0x13a
0x124 disk[1].owner_cfg_num: 0x0
0x138 disk[2].serial: "        6TE095KM"
0x148 disk[2].totalBlocks: 1953525168
0x14c disk[2].scsiId: 0x30000
0x150 disk[2].status: 0x13a
0x154 disk[2].owner_cfg_num: 0x0
0x168 disk[3].serial: "        6TE0EYCK"
0x178 disk[3].totalBlocks: 1953525168
0x17c disk[3].scsiId: 0x20000
0x180 disk[3].status: 0x13a
0x184 disk[3].owner_cfg_num: 0x0
0x198 disk[4].serial: "        9TE162KC"
0x1a8 disk[4].totalBlocks: 1953525168
0x1ac disk[4].scsiId: 0x50000
0x1b0 disk[4].status: 0x13a
0x1b4 disk[4].owner_cfg_num: 0x0
0x1c8 isw_dev[0].volume: "             5TB"
0x1dc isw_dev[0].SizeHigh: 2
0x1d8 isw_dev[0].SizeLow: 1177665536
0x1e0 isw_dev[0].status: 0xc
0x1e4 isw_dev[0].reserved_blocks: 0
0x1e8 isw_dev[0].migr_priority: 0
0x1e9 isw_dev[0].num_sub_vol: 0
0x1ea isw_dev[0].tid: 1
0x1eb isw_dev[0].cng_master_disk: 0
0x1ec isw_dev[0].cache_policy: 0
0x1ee isw_dev[0].cng_state: 0
0x1ef isw_dev[0].cng_sub_state: 0
0x218 isw_dev[0].vol.curr_migr_unit: 0
0x21c isw_dev[0].vol.check_point_id: 0
0x220 isw_dev[0].vol.migr_state: 0
0x221 isw_dev[0].vol.migr_type: 0
0x222 isw_dev[0].vol.dirty: 0
0x223 isw_dev[0].vol.fs_state: 255
0x224 isw_dev[0].vol.verify_errors: 0
0x226 isw_dev[0].vol.verify_bad_blocks: 0
0x238 isw_dev[0].vol.map[0].pba_of_lba0: 0
0x23c isw_dev[0].vol.map[0].blocks_per_member: 1953520392
0x240 isw_dev[0].vol.map[0].num_data_stripes: 7630938
0x244 isw_dev[0].vol.map[0].blocks_per_strip: 256
0x246 isw_dev[0].vol.map[0].map_state: 0
0x247 isw_dev[0].vol.map[0].raid_level: 0
0x248 isw_dev[0].vol.map[0].num_members: 5
0x249 isw_dev[0].vol.map[0].num_domains: 1
0x24a isw_dev[0].vol.map[0].failed_disk_num: 255
0x24b isw_dev[0].vol.map[0].ddf: 1
0x268 isw_dev[0].vol.map[0].disk_ord_tbl[0]: 0x0
0x26c isw_dev[0].vol.map[0].disk_ord_tbl[1]: 0x1
0x270 isw_dev[0].vol.map[0].disk_ord_tbl[2]: 0x2
0x274 isw_dev[0].vol.map[0].disk_ord_tbl[3]: 0x3
0x278 isw_dev[0].vol.map[0].disk_ord_tbl[4]: 0x4

/dev/sda (isw):
0x000 sig: "  Intel Raid ISM Cfg Sig. 1.3.00"
0x020 check_sum: 3075215238
0x024 mpb_size: 636
0x028 family_num: 839860073
0x02c generation_num: 2222
0x030 error_log_size: 4080
0x034 attributes: 2684354561
0x038 num_disks: 5
0x039 num_raid_devs: 1
0x03a error_log_pos: 2
0x03c cache_size: 1899642679
0x040 orig_family_num: 839860073
0x044 power_cycle_count: 554091059
0x048 bbm_log_size: 0
0x0d8 disk[0].serial: "        9TE1BPDN"
0x0e8 disk[0].totalBlocks: 1953525168
0x0ec disk[0].scsiId: 0x10000
0x0f0 disk[0].status: 0x13a
0x0f4 disk[0].owner_cfg_num: 0x0
0x108 disk[1].serial: "        6TE09CNQ"
0x118 disk[1].totalBlocks: 1953525168
0x11c disk[1].scsiId: 0x20000
0x120 disk[1].status: 0x13a
0x124 disk[1].owner_cfg_num: 0x0
0x138 disk[2].serial: "        6TE095KM"
0x148 disk[2].totalBlocks: 1953525168
0x14c disk[2].scsiId: 0x30000
0x150 disk[2].status: 0x13a
0x154 disk[2].owner_cfg_num: 0x0
0x168 disk[3].serial: "        6TE0EYCK"
0x178 disk[3].totalBlocks: 1953525168
0x17c disk[3].scsiId: 0x40000
0x180 disk[3].status: 0x13a
0x184 disk[3].owner_cfg_num: 0x0
0x198 disk[4].serial: "        9TE162KC"
0x1a8 disk[4].totalBlocks: 1953525168
0x1ac disk[4].scsiId: 0x10000
0x1b0 disk[4].status: 0x13a
0x1b4 disk[4].owner_cfg_num: 0x0
0x1c8 isw_dev[0].volume: "             5TB"
0x1dc isw_dev[0].SizeHigh: 2
0x1d8 isw_dev[0].SizeLow: 1177665536
0x1e0 isw_dev[0].status: 0xc
0x1e4 isw_dev[0].reserved_blocks: 0
0x1e8 isw_dev[0].migr_priority: 0
0x1e9 isw_dev[0].num_sub_vol: 0
0x1ea isw_dev[0].tid: 1
0x1eb isw_dev[0].cng_master_disk: 0
0x1ec isw_dev[0].cache_policy: 0
0x1ee isw_dev[0].cng_state: 0
0x1ef isw_dev[0].cng_sub_state: 0
0x218 isw_dev[0].vol.curr_migr_unit: 0
0x21c isw_dev[0].vol.check_point_id: 0
0x220 isw_dev[0].vol.migr_state: 0
0x221 isw_dev[0].vol.migr_type: 0
0x222 isw_dev[0].vol.dirty: 0
0x223 isw_dev[0].vol.fs_state: 255
0x224 isw_dev[0].vol.verify_errors: 0
0x226 isw_dev[0].vol.verify_bad_blocks: 0
0x238 isw_dev[0].vol.map[0].pba_of_lba0: 0
0x23c isw_dev[0].vol.map[0].blocks_per_member: 1953520392
0x240 isw_dev[0].vol.map[0].num_data_stripes: 7630938
0x244 isw_dev[0].vol.map[0].blocks_per_strip: 256
0x246 isw_dev[0].vol.map[0].map_state: 0
0x247 isw_dev[0].vol.map[0].raid_level: 0
0x248 isw_dev[0].vol.map[0].num_members: 5
0x249 isw_dev[0].vol.map[0].num_domains: 1
0x24a isw_dev[0].vol.map[0].failed_disk_num: 255
0x24b isw_dev[0].vol.map[0].ddf: 1
0x268 isw_dev[0].vol.map[0].disk_ord_tbl[0]: 0x0
0x26c isw_dev[0].vol.map[0].disk_ord_tbl[1]: 0x1
0x270 isw_dev[0].vol.map[0].disk_ord_tbl[2]: 0x2
0x274 isw_dev[0].vol.map[0].disk_ord_tbl[3]: 0x3
0x278 isw_dev[0].vol.map[0].disk_ord_tbl[4]: 0x4

```

---

### Post by Zwany on 2011-04-17
At this point I will repartition it on linux with a ntfs file system

---

### Post by psusi on 2011-04-17
Can you post the output of:

```
sudo dmsetup table
```

---

### Post by Zwany on 2011-04-19
isw_idjigaahd_5TB: 0 9767601920 striped 5 256 8:80 0 8:48 0 8:32 0 8:16 0 8:0 0

---

### Post by psusi on 2011-04-19
One more command:

```
sudo hdparm -i /dev/sd?
```

---

### Post by Zwany on 2011-04-24
```
/dev/sda:

 Model=ST31000333AS, FwRev=CC1H, SerialNo=9TE162KC
 Config={ HardSect NotMFM HdSw>15uSec Fixed DTR>10Mbs RotSpdTol>.5% }
 RawCHS=16383/16/63, TrkSize=0, SectSize=0, ECCbytes=4
 BuffType=unknown, BuffSize=unknown, MaxMultSect=16, MultSect=off
 CurCHS=16383/16/63, CurSects=16514064, LBA=yes, LBAsects=1953525168
 IORDY=on/off, tPIO={min:120,w/IORDY:120}, tDMA={min:120,rec:120}
 PIO modes:  pio0 pio1 pio2 pio3 pio4 
 DMA modes:  mdma0 mdma1 mdma2 
 UDMA modes: udma0 udma1 udma2 udma3 udma4 udma5 *udma6 
 AdvancedPM=no WriteCache=enabled
 Drive conforms to: unknown:  ATA/ATAPI-4,5,6,7

 * signifies the current active mode


/dev/sdb:

 Model=ST31000333AS, FwRev=CC1F, SerialNo=6TE0EYCK
 Config={ HardSect NotMFM HdSw>15uSec Fixed DTR>10Mbs RotSpdTol>.5% }
 RawCHS=16383/16/63, TrkSize=0, SectSize=0, ECCbytes=4
 BuffType=unknown, BuffSize=unknown, MaxMultSect=16, MultSect=off
 CurCHS=16383/16/63, CurSects=16514064, LBA=yes, LBAsects=1953525168
 IORDY=on/off, tPIO={min:120,w/IORDY:120}, tDMA={min:120,rec:120}
 PIO modes:  pio0 pio1 pio2 pio3 pio4 
 DMA modes:  mdma0 mdma1 mdma2 
 UDMA modes: udma0 udma1 udma2 udma3 udma4 udma5 *udma6 
 AdvancedPM=no WriteCache=enabled
 Drive conforms to: unknown:  ATA/ATAPI-4,5,6,7

 * signifies the current active mode


/dev/sdc:

 Model=ST31000333AS, FwRev=CC1F, SerialNo=6TE095KM
 Config={ HardSect NotMFM HdSw>15uSec Fixed DTR>10Mbs RotSpdTol>.5% }
 RawCHS=16383/16/63, TrkSize=0, SectSize=0, ECCbytes=4
 BuffType=unknown, BuffSize=unknown, MaxMultSect=16, MultSect=off
 CurCHS=16383/16/63, CurSects=16514064, LBA=yes, LBAsects=1953525168
 IORDY=on/off, tPIO={min:120,w/IORDY:120}, tDMA={min:120,rec:120}
 PIO modes:  pio0 pio1 pio2 pio3 pio4 
 DMA modes:  mdma0 mdma1 mdma2 
 UDMA modes: udma0 udma1 udma2 udma3 udma4 udma5 *udma6 
 AdvancedPM=no WriteCache=enabled
 Drive conforms to: unknown:  ATA/ATAPI-4,5,6,7

 * signifies the current active mode


/dev/sdd:

 Model=ST31000333AS, FwRev=CC1F, SerialNo=6TE09CNQ
 Config={ HardSect NotMFM HdSw>15uSec Fixed DTR>10Mbs RotSpdTol>.5% }
 RawCHS=16383/16/63, TrkSize=0, SectSize=0, ECCbytes=4
 BuffType=unknown, BuffSize=unknown, MaxMultSect=16, MultSect=off
 CurCHS=16383/16/63, CurSects=16514064, LBA=yes, LBAsects=1953525168
 IORDY=on/off, tPIO={min:120,w/IORDY:120}, tDMA={min:120,rec:120}
 PIO modes:  pio0 pio1 pio2 pio3 pio4 
 DMA modes:  mdma0 mdma1 mdma2 
 UDMA modes: udma0 udma1 udma2 udma3 udma4 udma5 *udma6 
 AdvancedPM=no WriteCache=enabled
 Drive conforms to: unknown:  ATA/ATAPI-4,5,6,7

 * signifies the current active mode


/dev/sde:

 Model=WDC WD3000GLFS-01F8U0, FwRev=03.03V01, SerialNo=WD-WXL408033486
 Config={ HardSect NotMFM HdSw>15uSec SpinMotCtl Fixed DTR>5Mbs FmtGapReq }
 RawCHS=16383/16/63, TrkSize=0, SectSize=0, ECCbytes=52
 BuffType=unknown, BuffSize=16384kB, MaxMultSect=16, MultSect=off
 CurCHS=16383/16/63, CurSects=16514064, LBA=yes, LBAsects=586072368
 IORDY=on/off, tPIO={min:120,w/IORDY:120}, tDMA={min:120,rec:120}
 PIO modes:  pio0 pio3 pio4 
 DMA modes:  mdma0 mdma1 mdma2 
 UDMA modes: udma0 udma1 udma2 udma3 udma4 udma5 *udma6 
 AdvancedPM=no WriteCache=enabled
 Drive conforms to: Unspecified:  ATA/ATAPI-1,2,3,4,5,6,7

 * signifies the current active mode


/dev/sdf:

 Model=ST31000333AS, FwRev=CC1H, SerialNo=9TE1BPDN
 Config={ HardSect NotMFM HdSw>15uSec Fixed DTR>10Mbs RotSpdTol>.5% }
 RawCHS=16383/16/63, TrkSize=0, SectSize=0, ECCbytes=4
 BuffType=unknown, BuffSize=unknown, MaxMultSect=16, MultSect=off
 CurCHS=16383/16/63, CurSects=16514064, LBA=yes, LBAsects=1953525168
 IORDY=on/off, tPIO={min:120,w/IORDY:120}, tDMA={min:120,rec:120}
 PIO modes:  pio0 pio1 pio2 pio3 pio4 
 DMA modes:  mdma0 mdma1 mdma2 
 UDMA modes: udma0 udma1 udma2 udma3 udma4 udma5 *udma6 
 AdvancedPM=no WriteCache=enabled
 Drive conforms to: unknown:  ATA/ATAPI-4,5,6,7

 * signifies the current active mode


/dev/sdg:
 HDIO_DRIVE_CMD(identify) failed: Invalid exchange
 HDIO_GET_IDENTITY failed: Invalid argument

```

---

### Post by Zwany on 2011-04-24
Can't even format the thing: ```
Error creating partition table: helper exited with exit code 1: In part_create_partition_table: device_file=/dev/dm-0, scheme=3
got it
got disk
committed to disk
BLKRRPART ioctl failed for /dev/dm-0: Invalid argument
```

Or partition it:

```
Error creating partition: helper exited with exit code 1: In part_add_partition: device_file=/dev/dm-0, start=0, size=5001012183040, type=EBD0A0A2-B9E5-4433-87C0-68B6B72699C7
Entering MS-DOS parser (offset=0, size=5001012183040)
MSDOS_MAGIC found
found partition type 0xee => protective MBR for GPT
Exiting MS-DOS parser
Entering EFI GPT parser
GPT magic found
partition_entry_lba=2
num_entries=128
size_of_entry=128
Leaving EFI GPT parser
EFI GPT partition table detected
containing partition table scheme = 3
got it
got disk
new partition
added partition start=17408 size=5001012148736
committed to disk
Error doing BLKPG ioctl with BLKPG_ADD_PARTITION for partition 1 of size 17408 at offset 5001012148736 on /dev/dm-0: Invalid argument
```

---

### Post by Zwany on 2011-04-24
I can format it and use it under opensuse and it works fine. BUT NOT UBUNTU! god this is driving me insane. why cant anyone help me?

---

### Post by psusi on 2011-04-25
What program were you using there?  It does not appear to know how to properly partition a dmraid device, but does seem to recognize the partition table.  Also were you running that in Ubuntu or opensuse?

What I am confused about is the proper order the disks are supposed to be assembled in.  According to the serial numbers in the raid metadata and hdparm -i, the order should be sdf sdd sdc sdb sda, which is the order being used according to dmsetup, but fdisk should see a partition table on the first disk, but instead of seeing it on sdf, it saw it on sda.

If opensuse recognizes the partitions, from there can you run dmsetup table and hdparm -i /dev/sd? again so we can compare with Ubuntu?

---

### Post by Zwany on 2011-04-26
> **psusi said:**
> What program were you using there?  It does not appear to know how to properly partition a dmraid device, but does seem to recognize the partition table.

I was using 'disk utility' within ubuntu

> Also were you running that in Ubuntu or opensuse? Ill specify when I'm not using ubuntu, so far all outputs are from ubuntu 10.10

> What I am confused about is the proper order the disks are supposed to be assembled in.  According to the serial numbers in the raid metadata and hdparm -i, the order should be sdf sdd sdc sdb sda, which is the order being used according to dmsetup, but fdisk should see a partition table on the first disk, but instead of seeing it on sdf, it saw it on sda.

If opensuse recognizes the partitions, from there can you run dmsetup table and hdparm -i /dev/sd? again so we can compare with Ubuntu?

Opensuse has now stop recognising the drive after I copied back my files oddly. I get this output when I try and mount it:```
mount /dev/mapper/isw_idjigaahd_5TB_part1 Raid/ -t ntfs
ntfs_mst_post_read_fixup: magic: 0x507fa08c  size: 1024  usa_ofs: 32842  usa_count: 41668: Invalid argument
ntfs_mst_post_read_fixup: magic: 0x72ad8a9d  size: 1024  usa_ofs: 58664  usa_count: 38413: Invalid argument
ntfs_mst_post_read_fixup: magic: 0x4a0eac08  size: 1024  usa_ofs: 13772  usa_count: 40850: Invalid argument
ntfs_mst_post_read_fixup: magic: 0xf368bde6  size: 1024  usa_ofs: 30250  usa_count: 54168: Invalid argument
$MFTMirr error: Invalid mft record for '$MFT'.
Failed to mount '/dev/dm-1': Input/output error
NTFS is either inconsistent, or there is a hardware fault, or it's a
SoftRAID/FakeRAID hardware. In the first case run chkdsk /f on Windows
then reboot into Windows twice. The usage of the /f parameter is very
important! If the device is a SoftRAID/FakeRAID then first activate
it and mount a different device under the /dev/mapper/ directory, (e.g.
/dev/mapper/nvidia_eahaabcc1). Please see the 'dmraid' documentation
for more details.

```

**Opensuse**

dmsetup status:```
isw_idjigaahd_5TB_part1: 0 9767598080 linear 
isw_idjigaahd_5TB_part1p3: 0 1663071081 linear 
isw_idjigaahd_5TB_part1p2: 0 778921332 linear 
isw_idjigaahd_5TB_part1p1: 0 1953719666 linear 
isw_idjigaahd_5TB: 0 9767600640 striped 5 8:80 8:48 8:32 8:16 8:0 1 AAAAA

```

**Opensuse**

hdparm -i /dev/sd?:```
/dev/sda:

 Model=ST31000333AS, FwRev=CC1H, SerialNo=9TE162KC
 Config={ HardSect NotMFM HdSw>15uSec Fixed DTR>10Mbs RotSpdTol>.5% }
 RawCHS=16383/16/63, TrkSize=0, SectSize=0, ECCbytes=4
 BuffType=unknown, BuffSize=unknown, MaxMultSect=16, MultSect=off
 CurCHS=16383/16/63, CurSects=16514064, LBA=yes, LBAsects=1953525168
 IORDY=on/off, tPIO={min:120,w/IORDY:120}, tDMA={min:120,rec:120}
 PIO modes:  pio0 pio1 pio2 pio3 pio4 
 DMA modes:  mdma0 mdma1 mdma2 
 UDMA modes: udma0 udma1 udma2 udma3 udma4 udma5 *udma6 
 AdvancedPM=no WriteCache=enabled
 Drive conforms to: unknown:  ATA/ATAPI-4,5,6,7

 * signifies the current active mode


/dev/sdb:

 Model=ST31000333AS, FwRev=CC1F, SerialNo=6TE0EYCK
 Config={ HardSect NotMFM HdSw>15uSec Fixed DTR>10Mbs RotSpdTol>.5% }
 RawCHS=16383/16/63, TrkSize=0, SectSize=0, ECCbytes=4
 BuffType=unknown, BuffSize=unknown, MaxMultSect=16, MultSect=off
 CurCHS=16383/16/63, CurSects=16514064, LBA=yes, LBAsects=1953525168
 IORDY=on/off, tPIO={min:120,w/IORDY:120}, tDMA={min:120,rec:120}
 PIO modes:  pio0 pio1 pio2 pio3 pio4 
 DMA modes:  mdma0 mdma1 mdma2 
 UDMA modes: udma0 udma1 udma2 udma3 udma4 udma5 *udma6 
 AdvancedPM=no WriteCache=enabled
 Drive conforms to: unknown:  ATA/ATAPI-4,5,6,7

 * signifies the current active mode


/dev/sdc:

 Model=ST31000333AS, FwRev=CC1F, SerialNo=6TE095KM
 Config={ HardSect NotMFM HdSw>15uSec Fixed DTR>10Mbs RotSpdTol>.5% }
 RawCHS=16383/16/63, TrkSize=0, SectSize=0, ECCbytes=4
 BuffType=unknown, BuffSize=unknown, MaxMultSect=16, MultSect=off
 CurCHS=16383/16/63, CurSects=16514064, LBA=yes, LBAsects=1953525168
 IORDY=on/off, tPIO={min:120,w/IORDY:120}, tDMA={min:120,rec:120}
 PIO modes:  pio0 pio1 pio2 pio3 pio4 
 DMA modes:  mdma0 mdma1 mdma2 
 UDMA modes: udma0 udma1 udma2 udma3 udma4 udma5 *udma6 
 AdvancedPM=no WriteCache=enabled
 Drive conforms to: unknown:  ATA/ATAPI-4,5,6,7

 * signifies the current active mode


/dev/sdd:

 Model=ST31000333AS, FwRev=CC1F, SerialNo=6TE09CNQ
 Config={ HardSect NotMFM HdSw>15uSec Fixed DTR>10Mbs RotSpdTol>.5% }
 RawCHS=16383/16/63, TrkSize=0, SectSize=0, ECCbytes=4
 BuffType=unknown, BuffSize=unknown, MaxMultSect=16, MultSect=off
 CurCHS=16383/16/63, CurSects=16514064, LBA=yes, LBAsects=1953525168
 IORDY=on/off, tPIO={min:120,w/IORDY:120}, tDMA={min:120,rec:120}
 PIO modes:  pio0 pio1 pio2 pio3 pio4 
 DMA modes:  mdma0 mdma1 mdma2 
 UDMA modes: udma0 udma1 udma2 udma3 udma4 udma5 *udma6 
 AdvancedPM=no WriteCache=enabled
 Drive conforms to: unknown:  ATA/ATAPI-4,5,6,7

 * signifies the current active mode


/dev/sde:

 Model=WDC WD3000GLFS-01F8U0, FwRev=03.03V01, SerialNo=WD-WXL408033486
 Config={ HardSect NotMFM HdSw>15uSec SpinMotCtl Fixed DTR>5Mbs FmtGapReq }
 RawCHS=16383/16/63, TrkSize=0, SectSize=0, ECCbytes=52
 BuffType=unknown, BuffSize=16384kB, MaxMultSect=16, MultSect=off
 CurCHS=16383/16/63, CurSects=16514064, LBA=yes, LBAsects=586072368
 IORDY=on/off, tPIO={min:120,w/IORDY:120}, tDMA={min:120,rec:120}
 PIO modes:  pio0 pio3 pio4 
 DMA modes:  mdma0 mdma1 mdma2 
 UDMA modes: udma0 udma1 udma2 udma3 udma4 udma5 *udma6 
 AdvancedPM=no WriteCache=enabled
 Drive conforms to: Unspecified:  ATA/ATAPI-1,2,3,4,5,6,7

 * signifies the current active mode


/dev/sdf:

 Model=ST31000333AS, FwRev=CC1H, SerialNo=9TE1BPDN
 Config={ HardSect NotMFM HdSw>15uSec Fixed DTR>10Mbs RotSpdTol>.5% }
 RawCHS=16383/16/63, TrkSize=0, SectSize=0, ECCbytes=4
 BuffType=unknown, BuffSize=unknown, MaxMultSect=16, MultSect=off
 CurCHS=16383/16/63, CurSects=16514064, LBA=yes, LBAsects=1953525168
 IORDY=on/off, tPIO={min:120,w/IORDY:120}, tDMA={min:120,rec:120}
 PIO modes:  pio0 pio1 pio2 pio3 pio4 
 DMA modes:  mdma0 mdma1 mdma2 
 UDMA modes: udma0 udma1 udma2 udma3 udma4 udma5 *udma6 
 AdvancedPM=no WriteCache=enabled
 Drive conforms to: unknown:  ATA/ATAPI-4,5,6,7

 * signifies the current active mode


/dev/sdg:
SG_IO: bad/missing sense data, sb[]:  70 00 0b 00 00 00 00 0a 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
 HDIO_GET_IDENTITY failed: Invalid argument


```

**Opensuse**

sudo parted /dev/mapper/isw_idjigaahd_5TB print:
```
GNU Parted 2.3
Using /dev/mapper/isw_idjigaahd_5TB
Welcome to GNU Parted! Type 'help' to view a list of commands.
(parted) print
Model: Linux device-mapper (striped) (dm)
Disk /dev/mapper/isw_idjigaahd_5TB: 5001GB
Sector size (logical/physical): 512B/512B
Partition Table: gpt

Number  Start  End     Size    File system  Name     Flags
 1      655kB  5001GB  5001GB  ntfs         primary

```

---

### Post by Zwany on 2011-04-26
Just for fun
[B]
Windows 7

[/B]```
D:\>chkdsk /f
The type of the file system is NTFS.
Cannot lock current drive.

Chkdsk cannot run because the volume is in use by another
process.  Chkdsk may run if this volume is dismounted first.
ALL OPENED HANDLES TO THIS VOLUME WOULD THEN BE INVALID.
Would you like to force a dismount on this volume? (Y/N) y
Volume dismounted.  All opened handles to this volume are now invalid.
Volume label is Backup.

CHKDSK is verifying files (stage 1 of 3)...
  357888 file records processed.
File verification completed.
  8 large file records processed.
  0 bad file records processed.
  0 EA records processed.
  0 reparse records processed.
CHKDSK is verifying indexes (stage 2 of 3)...
  395156 index entries processed.
Index verification completed.
  0 unindexed files scanned.
  0 unindexed files recovered.
CHKDSK is verifying security descriptors (stage 3 of 3)...
  357888 file SDs/SIDs processed.
Security descriptor verification completed.
  18634 data files processed.
Windows has checked the file system and found no problems.

   4768241 MB total disk space.
   4186555 MB in 339040 files.
    131368 KB in 18636 indexes.
         0 KB in bad sectors.
    930774 KB in use by the system.
     65536 KB occupied by the log file.
 594585168 KB available on disk.

      4096 bytes in each allocation unit.
1220669951 total allocation units on disk.
 148646292 allocation units available on disk.
```

---

### Post by psusi on 2011-04-26
There seem to be several problems going on here.  First, under open suse, it appears to be somehow recognizing partitions inside the NTFS partition, which is not possible.  Since you also now are getting those errors trying to mount it, I think you may have corrupted the boot sector by trying to partition the partition.

More importantly, it appears that Ubuntu is using the wrong total length for the array, which would cause parted to be unable to find the backup copy of the gpt.  I am still not sure why fdisk does not see the protective mbr on the array, and why it sees it on sda instead of sdf, but there is definitely a bug in Ubuntu's dmraid.

Please run sudo dmraid -rD.  This will dump the raid metadata to files in a directory that should be named dmraid.isw.  Please tar and gzip this directory and file a bug report and attach that file.

[https://bugs.launchpad.net/ubuntu/+source/dmraid/+filebug](https://bugs.launchpad.net/ubuntu/+source/dmraid/+filebug)

I suggest this for the Subject and description:

```
isw: incorrect stripe length calculated
```

```
Per this thread on the forums:
[http://ubuntuforums.org/showthread.php?p=10721775#post10721775](http://ubuntuforums.org/showthread.php?p=10721775#post10721775)

OpenSuse configures the array with one length and recognizes the partition table:

isw_idjigaahd_5TB: 0 9767600640 striped 5 8:80 8:48 8:32 8:16 8:0 1 AAAAA 9767601960

And Ubuntu seems to configure it to be too long and can not recognize the partition table:

isw_idjigaahd_5TB: 0 9767601920 striped 5 256 8:80 0 8:48 0 8:32 0 8:16 0 8:0 0
```

Now that I look at this one more time, I noticed that you did dmsetup table on ubuntu, but dmsetup status on opensuse.  Can you also run dmsetup status on ubuntu, and dmsetup table on opensuse?

As for your partitions, let's try and take a close look and figure out what seems to be going on.  Please post the output ( here, not in the bug report ) of:

```
sudo dd bs=512 count=2 if=/dev/sda 2>/dev/null | hd
```

Repeat for the other drives ( sdb, sdc, sdd, sdf ).

---

