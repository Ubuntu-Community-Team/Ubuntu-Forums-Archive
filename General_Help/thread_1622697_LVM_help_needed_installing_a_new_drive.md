---
title: "LVM help needed installing a new drive"
date: 2010-11-15
forum: General Help
---

### Post by flycast on 2010-11-15
I have been reading these fine howtos [here]("http://www.howtoforge.com/linux_lvm") and [here]("https://wiki.ubuntu.com/Lvm"). I thought that I did all as specified. The issue is the new capacity shows up in the logical volume but not when I browse to the folder from the network. 

fdisk:
> Disk /dev/sda: 160.0 GB, 160000000000 bytes
255 heads, 63 sectors/track, 19452 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000a25c0

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1          32      248832   83  Linux
Partition 1 does not end on cylinder boundary.
/dev/sda2              32       19453   155998209    5  Extended
/dev/sda5              32       19453   155998208   8e  Linux LVM

WARNING: GPT (GUID Partition Table) detected on '/dev/sdb'! The util fdisk doesn't support GPT. Use GNU Parted.


Disk /dev/sdb: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1      121601   976760001   8e  Linux LVM

fstab:
> # /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
/dev/mapper/server-root /               ext4    errors=remount-ro 0       1
# /boot was on /dev/sda1 during installation
UUID=b8425e9b-d771-4019-99f2-e211a9bd7818 /boot           ext2    defaults        0       2
/dev/mapper/server-home /home           ext4    defaults,usrquota,grpquota,acl        0       2
/dev/mapper/server-swap_1 none            swap    sw              0       0


vgdisplay:
>   --- Volume group ---
  VG Name               server
  System ID             
  Format                lvm2
  Metadata Areas        2
  Metadata Sequence No  7
  VG Access             read/write
  VG Status             resizable
  MAX LV                0
  Cur LV                3
  Open LV               3
  Max PV                0
  Cur PV                2
  Act PV                2
  VG Size               1.05 TiB
  PE Size               4.00 MiB
  Total PE              276551
  Alloc PE / Size       258398 / 1009.37 GiB
  Free  PE / Size       18153 / 70.91 GiB
  VG UUID               cDNbpe-MiHt-pQOP-ZdCL-1k30-oKYS-IhJboo


lvdisplay:
>  --- Logical volume ---
  LV Name                /dev/server/root
  VG Name                server
  LV UUID                ft0eUY-f0Gc-eLYn-1BTd-fQa6-Mniu-2G08AL
  LV Write Access        read/write
  LV Status              available
  # open                 1
  LV Size                6.52 GiB
  Current LE             1668
  Segments               1
  Allocation             inherit
  Read ahead sectors     auto
  - currently set to     256
  Block device           252:0
   
  --- Logical volume ---
  LV Name                /dev/server/swap_1
  VG Name                server
  LV UUID                39svas-hp1v-up29-3Nm9-chkP-6lHQ-4SSQmU
  LV Write Access        read/write
  LV Status              available
  # open                 1
  LV Size                2.85 GiB
  Current LE             730
  Segments               1
  Allocation             inherit
  Read ahead sectors     auto
  - currently set to     256
  Block device           252:1
   
  --- Logical volume ---
  LV Name                /dev/server/home
  VG Name                server
  LV UUID                ui1U7y-pH2L-ZDYd-Z4Fe-AOUj-cup8-lU2sdW
  LV Write Access        read/write
  LV Status              available
  # open                 1
  LV Size                1000.00 GiB
  Current LE             256000
  Segments               2
  Allocation             inherit
  Read ahead sectors     auto
  - currently set to     256
  Block device           252:2


Here is what I am confused about...in fstab the LVM2 volume where my current data is mounted at /dev/mapper/server-home but the logical volume is /dev/server/home.

Why is my additional drive showing up in the logical volume but not as additional capacity in the /home folder?

---

### Post by flycast on 2010-11-16
What? No LVM experts out there?

---

### Post by psusi on 2010-11-16
After you expand the logical volume, you need to expand the filesystem stored in it.  Assuming it is ext[234], you need to run resize2fs.  If the mount point is defined in your /etc/fstab, then you can just run sudo resize2fs /path/to/mount and it will expand it to use the full space immediately while the volume is mounted.

---

### Post by nunrgguy on 2010-11-17
If you get one of the GUIs you'll be able to see what is happening. It sounds like maybe you've added the new drive to the vg but haven't expanded into it yet

---

### Post by srs5694 on 2010-11-17
A few more comments:


[list]
[*]The /dev/mapper/volgroup-volname file is the "real" logical volume device (in Ubuntu, anyhow), and /dev/volgroup/volname is a symbolic link "shortcut" to this file. You can use either name in most operations. The latter is obviously shorter and so may be preferred in some situations.
[*]GUI front-ends to LVM include system-config-lvm and kvpm. IIRC, both are available via the Ubuntu APT repositories.
[*]Your /dev/sdb appears to be a Master Boot Record (MBR) disk with leftover GUID Partition Table (GPT) data from previous use in a Mac or experimentation with GPT. Linux is reading it OK for the moment, but some disk utilities (such as anything based on libparted, including GParted) will most likely flake out on this disk. I strongly recommend that you fix this, as described [in this post of mine](http://ubuntuforums.org/showpost.php?p=10022223&postcount=34) in another thread. Alternatively, you could convert it into a GPT disk, but you'll probably have to convert the MBR data to GPT form (I can't tell what's currently in the GPT).
[/list]

---

### Post by flycast on 2010-11-17
psusi - that did the trick.

srs5694 - Thanks for the heads up. Ijust took the disk and repartitioned it. I installed kvpm and it worked great. Thanks for the help! The volume is now resized and working properly!

---

