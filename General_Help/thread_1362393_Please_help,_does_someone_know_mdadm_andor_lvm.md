---
title: "Please help, does someone know mdadm and/or lvm ???"
date: 2009-12-23
forum: General Help
---

### Post by Th3Professor on 2009-12-23
I tested the Ubuntu 9.10 Live CD's ability to recognize my current RAID 5 and LVM set-up and it did *not* recognize it. Do I need a kernel tweak? Do I need to enter some mdadm and/or lvm-related commands? I'm going to install Ubuntu Studio 9.10 but that install DVD is not a Live DVD. So, I burned a Ubuntu 9.10 Live CD and tested it out. It just sees multiple separate hard drives, it has no idea that there is either a raid or lvm configuration set up on those hard drives.

Surely there is *someone* in the Ubuntu community who knows mdadm and/or lvm.

I'm not going to upgrade to 9.10, I'm currently using "Ubustu" 8.10 and it is kind of buggy anyway, so a fresh install is necessary.

What steps should I take with mdadm and lvm **before** installing Ubuntu (or Ubuntu Studio) 9.10?

What steps should I take with mdadm and lvm **after** installing Ubuntu (or Ubuntu Studio) 9.10?

Please help! Someone? :(

---

### Post by QrK0 on 2009-12-23
I think it is not installed by default in the live-cd. So once you have the live session initiated, you can install mdadm and lvm2:

```
$ sudo apt-get install mdadm lvm2
```

After install those tools, you can assemble the existing raid and finally scan for the lvm:

```
$ sudo mdadm --assemble
$ sudo vgchange -a y
```

Be careful, always make backups of your data before playing these kind of tools...

---

### Post by Th3Professor on 2009-12-23
> **QrK0 said:**
> I think it is not installed by default in the live-cd. So once you have the live session initiated, you can install mdadm and lvm2:

```
$ sudo apt-get install mdadm lvm2
```After install those tools, you can assemble the existing raid and finally scan for the lvm:

```
$ sudo mdadm --assemble
$ sudo vgchange -a y
```Be careful, always make backups of your data before playing these kind of tools...

:KS:KS:KS:KS:KS

Oh my god thank you!

update-

Will I need to do something like:

mdadm --assemble md-device options-and-component-devices...

and

vgchange --available [e|l] y
(either "e" or "l" for "exclusive" or "local")

...or would it be fine to just enter like you stated:

 sudo mdadm --assemble
sudo vgchange -a y

---

### Post by QrK0 on 2009-12-23
> **Th3Professor said:**
> :KS:KS:KS:KS:KS

Oh my god thank you!

update-

Will I need to do something like:

mdadm --assemble md-device options-and-component-devices...

and

vgchange --available [e|l] y
(either "e" or "l" for "exclusive" or "local")

...or would it be fine to just enter like you stated:

 sudo mdadm --assemble
sudo vgchange -a y

You should follow the man instructions, so for (re)assemble the raid the command is something like your post, in example:
```
$ sudo mdadm --assemble /dev/mdX --uuid='the uuid of the raid' /dev/sdY /dev/sdZ(where mdX is the device name of the raid you want to assemble and sdY sdZ the device names of the disk members)
```
or could be something like:
```
$ sudo mdadm --assemble --scan /dev/mdX --uuid='the uuid of the raid'
```
And about the LVM, the 'e' and 'l' options are for cluster environments. If no cluster is present, just issue the command
```
$ sudo vgchange -a y
```

I hope this helps!

---

### Post by Th3Professor on 2009-12-23
Here's some lvm scan/display info on the vg and pv, as well as df -h, fdisk -l, and the /etc/fstab...

```
# vgscan  
Reading all physical volumes.  This may take a while... 
Found volume group "vg0" using metadata type lvm2

# vgdisplay  
  --- Volume group --- 
  VG Name               vg0 
  System ID              
  Format                lvm2 
  Metadata Areas        1 
  Metadata Sequence No  6 
  VG Access             read/write 
  VG Status             resizable 
  MAX LV                0 
  Cur LV                3 
  Open LV               3 
  Max PV                0 
  Cur PV                1 
  Act PV                1 
  VG Size               931.52 GB 
  PE Size               4.00 MB 
  Total PE              238468 
  Alloc PE / Size       238468 / 931.52 GB 
  Free  PE / Size       0 / 0    
  VG UUID               q9qxE4-tp1X-PUZl-cWfE-PGI3-3y4X...

# pvscan  
PV /dev/md0   VG vg0   lvm2 [931.52 GB / 0    free] 
Total: 1 [931.52 GB] / in use: 1 [931.52 GB] / in no VG: 0 [0   ]

# pvdisplay  
  --- Physical volume --- 
  PV Name               /dev/md0 
  VG Name               vg0 
  PV Size               931.52 GB / not usable 2.75 MB 
  Allocatable           yes (but full) 
  PE Size (KByte)       4096 
  Total PE              238468 
  Free PE               0 
  Allocated PE          238468 
  PV UUID               Xw1LeW-LRbq-Xt0J-0XtR-fEfi-5LBk...

# df -h 
/dev/mapper/vg0-vault 
                      755G  293G  463G  39% /studio/vault 
/dev/mapper/vg0-zone   87G  184M   83G   1% /zone 
/dev/mapper/vg0-nomad 
                       87G  342M   82G   1% /nomad

# fdisk -l
Disk /dev/sdb: 500.1 GB, 500107862016 bytes 
255 heads, 63 sectors/track, 60801 cylinders 
Units = cylinders of 16065 * 512 = 8225280 bytes 
Disk identifier: 0x000c177d 
 
   Device Boot      Start         End      Blocks   Id  System 
/dev/sdb1               1       60801   488384001   fd  Linux raid autodetect 
 
Disk /dev/sdc: 500.1 GB, 500107862016 bytes 
255 heads, 63 sectors/track, 60801 cylinders 
Units = cylinders of 16065 * 512 = 8225280 bytes 
Disk identifier: 0x000caa62 
 
   Device Boot      Start         End      Blocks   Id  System 
/dev/sdc1               1       60801   488384001   fd  Linux raid autodetect 
 
Disk /dev/sdd: 500.1 GB, 500107862016 bytes 
255 heads, 63 sectors/track, 60801 cylinders 
Units = cylinders of 16065 * 512 = 8225280 bytes 
Disk identifier: 0x000d3415 
 
   Device Boot      Start         End      Blocks   Id  System 
/dev/sdd1               1       60801   488384001   fd  Linux raid autodetect

$ more /etc/fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda5
UUID=aab73c93-5c74-4252-b2db /               ext3    relatime,error
s=remount-ro 0       1
# /dev/sda1
UUID=90e2151d-168b-4918-9019 /boot           ext3    relatime      
  0       2
# /dev/sda6
UUID=a8097c76-3754-4c5a-8371 /studio/workspace ext3    relatime    
    0       2
# /dev/sda2
UUID=30DCC729DCC6 /windows        ntfs    defaults,umask=007,gid=46 0       
1
# /dev/sda7
UUID=43caaa32-d48f-414a-87b7 none            swap    sw            
  0       0
# /dev/sda8
UUID=8b3abdfd-a4cb-478d-b84d none            swap    sw            
  0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/vg0/vault  /studio/vault   xfs     rw,noatime      0       0
/dev/vg0/zone   /zone   ext3    rw,noatime      0       0
/dev/vg0/nomad  /nomad  ext3    rw,noatime      0       0

```The mdadm --assemble options are kind of confusing, with the uuid bit, then the bits about the sdY, sdZ, and mdX.

---

### Post by Th3Professor on 2009-12-23
Would the following steps work?

1. Install Ubuntu Studio 9.10 DVD (an alternate, not a "live" disc)
2. Install mdadm & lvm(2)
3. Enter the following commands:
$ sudo mdadm --assemble /dev/md0 --uuid=(*???*) /dev/sdb /dev/sdc /dev/sdd
$ sudo vgchange -a y
4. Copy old fstab file into new fstab file. (It can be backed up on another disk.)
5. Reboot

Where do I get the correct uuid for the mdadm re-assembly command?
Or is the fstab change really necessary?
Or will I need to still do some kind of "modprobe" for mdadm and/or lvm2?

---

### Post by QrK0 on 2009-12-24
All partitions in the same raid have the same uuid. When the raid is assembled, it have also the same uuid. To get the uuid you can enter
```
$ sudo mdadm -E /dev/sda1
```
Note that it is at partition level, if you examines the disk instead the partition, you will get no superblock information (anyway, the -E option is not destructive).
You can also make a copy of the file /etc/mdadm.conf, if it exists, and then restore to the new installation.

You can check the status of the raid devices entering:
```
$ sudo cat /proc/mdstat
```

---

### Post by Th3Professor on 2009-12-24
Thank you. That's a great idea - I went ahead and put the mdadm.conf into a google docs file for safe keeping 'til I get the new OS installed.

I did that with fstab too, do ya think I should just replace the new OS's fstab with the old one?

Does this look right:
```
$ sudo mdadm --assemble /dev/md0 --uuid=10056982:7e87ea13:b4ca6f73:30183c6d /dev/sdb /dev/sdc /dev/sdd
```and still just a simple "-a y" (?) on the lvm:
```
$ sudo vgchange -a y
```I found that really long string of uuid thing from your suggestion of using the "mdadm -E" command (examined sdb1/sdc1/sdd1.) Do you know if entering the uuid is really necessary?

I checked over on another board and someone mentioned the install should automatically detect and even associate itself with the raid/lvm disk set-up, though when I tested with a live cd it didn't recognize it. :-/ The same happened with a non-raid disk that is a separate partition, the live cd started to recognize that partition (a "workspace" directory) but when I clicked on it in a file browser window the directory disappeared.

This is that extra partition (for file storage) that disappeared:
# /dev/sda6
/studio/workspace ext3

---

### Post by QrK0 on 2009-12-24
The uuid information is recorded at disk level, so the mdadm process should recognise automatically the raid members. But I prefer to specify the uuid in the mdadm --assemble command, just to be sure...
But your mdadm command, I think is not correct. You should specify the partitions, not the disk. A disk could contains more than one partition...
The correct sentence should be:
```
$ sudo mdadm --assemble /dev/md0 --uuid=10056982:7e87ea13:b4ca6f73:30183c6d /dev/sdb1 /dev/sdc1 /dev/sdd1
```

The livecd does not come with mdadm nor lvm daemons, so it does not recognise the raid. For this reason, I suggested in my previous post to install them in the livecd session.
I don't remember right now if the installation process install those daemons automatically.
Just be careful to install the OS in the correct partition. You can install mdadm and lvm after.

Good luck!

---

### Post by Th3Professor on 2009-12-24
ubuntu@ubuntu:~$ sudo mdadm --assemble /dev/md0 --uuid=10056982:7e87ea13:b4ca6f73:30183c6d /dev/sdb1 /dev/sdc1 /dev/sdd1
mdadm: failed to add /dev/sdd1 to /dev/md0: Device or resource busy
mdadm: /dev/md0 assembled from 2 drives - need all 3 to start it (use --run to insist).

---

### Post by QrK0 on 2009-12-28
> **Th3Professor said:**
> 
mdadm: failed to add /dev/sdd1 to /dev/md0: Device or resource busy


Maybe the disk order is different when you starts from the livecd

---

