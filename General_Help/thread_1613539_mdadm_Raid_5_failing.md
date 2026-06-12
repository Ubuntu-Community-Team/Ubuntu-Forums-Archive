---
title: "mdadm Raid 5 failing"
date: 2010-11-04
forum: General Help
---

### Post by Captain_Intern on 2010-11-04
Hi,

I am having several issues with mdadm created arrays that do not initialize or mount on boot.

There is no data on the drives so I can hose them if need be.

My goal is to get 4x750gb hard drives running in a raid 5 configuration that starts up at boot time.

_This is the steps that I followed:_
Fdisk the drives
```
fdisk /dev/sd[bcde] 
WARNING: DOS-compatible mode is deprecated. It's strongly recommended to
         switch off the mode (command 'c') and change display units to
         sectors (command 'u').

Command (m for help): d
Selected partition 1

Command (m for help): n
Command action
   e   extended
   p   primary partition (1-4)
p
Partition number (1-4): 1
First cylinder (1-22794, default 1): 
Using default value 1
Last cylinder, +cylinders or +size{K,M,G} (1-22794, default 22794): 
Using default value 22794

Command (m for help): t
Selected partition 1
Hex code (type L to list codes): fd
Changed system type of partition 1 to fd (Linux raid autodetect)

Command (m for help): p
```

Rebooted the computer made the array
```
 mdadm --create /dev/md0 --chunk=256 --level=5 --raid-disks=4 --force /dev/sd[bcde]1

```

Checked the process
```
 cat /proc/mdstat
Personalities : [linear] [multipath] [raid0] [raid1] [raid6] [raid5] [raid4] [raid10]
md0 : active raid5 sdb1[0] sde1[3] sdd1[2] sdc1[1]
      2192871936 blocks level 5, 256k chunk, algorithm 2 [4/4] [UUUU]

```

Ran mkfs.ext4 it worked fine.
```

# pvcreate /dev/md0
# vgcreate DATA /dev/md0 

``` 

I rebooted the system and the array broke - it pulled /dev/sdbc1 and placed it in to md_d0

```
 mdadm --manage /dev/md_d0 --stop  
sudo mdadm -A /dev/md0 /dev/sdb1 /dev/sdc1 /dev/sdd1 /dev/sde1
sudo mount -a

```

```
 fdisk -L 

Disk /dev/sda: 150.0 GB, 150039945216 bytes
255 heads, 63 sectors/track, 18241 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x0002d863

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       17496   140530688   83  Linux
/dev/sda2           17496       18242     5990401    5  Extended
/dev/sda5           17496       18242     5990400   82  Linux swap / Solaris

Disk /dev/sdb: 750.2 GB, 750156374016 bytes
255 heads, 63 sectors/track, 91201 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x89215a2e

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       91000   730957468+  fd  Linux raid autodetect

Disk /dev/sdc: 750.2 GB, 750156374016 bytes
255 heads, 63 sectors/track, 91201 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xfc0c9421
  
 Device Boot      Start         End      Blocks   Id  System
/dev/sdc1               1       91000   730957468+  fd  Linux raid autodetect

Disk /dev/sdd: 750.2 GB, 750156374016 bytes
255 heads, 63 sectors/track, 91201 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x8b0d711d

   Device Boot      Start         End      Blocks   Id  System
/dev/sdd1               1       91000   730957468+  fd  Linux raid autodetect

Disk /dev/sde: 750.2 GB, 750156374016 bytes
255 heads, 63 sectors/track, 91201 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes


Disk identifier: 0xfe20bf12

   Device Boot      Start         End      Blocks   Id  System
/dev/sde1               1       91000   730957468+  fd  Linux raid autodetect

Disk /dev/md0: 2245.5 GB, 2245500862464 bytes
2 heads, 4 sectors/track, 548217984 cylinders
Units = cylinders of 8 * 512 = 4096 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 262144 bytes / 786432 bytes
Disk identifier: 0x00000000

Disk /dev/md0 doesn't contain a valid partition table

```

when I run /usr/share/mdadm/mkconf it provides this:
```
 
# mdadm.conf
#
# Please refer to mdadm.conf(5) for information about this file.
#

# by default, scan all partitions (/proc/partitions) for MD superblocks.
# alternatively, specify devices to scan, using wildcards if desired.
DEVICE partitions
/dev/sdb1 /dev/sdc1 /dev/sdd1 /dev/sde1

# auto-create devices with Debian standard permissions
CREATE owner=root group=disk mode=0660 auto=yes

# automatically tag new arrays as belonging to the local system
HOMEHOST <system>

# instruct the monitoring daemon where to send mail alerts
MAILADDR root

# definitions of existing MD arrays
ARRAY /dev/md0 level=raid5 num-devices=4 UUID=b4b8c310:f9dc688f:525e351a:5c9781a5
   spares=1
ARRAY /dev/md0 level=raid5 num-devices=4 UUID=be3e2fc0:c7fe50b6:525e351a:5c9781a5

```

I have attached my mdadm.conf file since it is different. 

Now my lvs and vgs do not show anything that exists anymore even after I created the volumes. 

I am really lost and confused to as what is happening and would appreciate any help that can be given.

---

