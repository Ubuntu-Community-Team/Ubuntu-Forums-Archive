---
title: "LVM - Reduce VG too much - is there a way to recover"
date: 2009-11-13
forum: General Help
---

### Post by lucy_t on 2009-11-13
OK I made a mistake and used vgreduce and reduced the size below that on the content contained in that vg. This managed to staop Ubuntu, forcing me to hard powercycle, leaving me with a machine that no longer recognises the VG, LV or PV's....

1. Is everything gone?
2. Is there a path to recovery? (I tried live boot and knoppix which showed me the LVM with nothing in it)

Help,

LT

---

### Post by lucy_t on 2009-11-13
The reason I got into this bother is that I used the default ubuntu install option with LVM. This makes the root the LVM, so when try to increase the LVM (say by adding a disk) you can get all the way until you need to unmount the volumne to expand it to fill the new space. So once I got there and failed to do this I was going to reduce the VG, backup the data, remove the disk, and rebuild with home on an LVM and everything else standard ext4...Darn I reduced the vlm too much by mistake and the system died.

Is there a way back?

---

### Post by lucy_t on 2009-11-15
Knoppix has given me a glimer of hope but I am not sure what I can/should be doing as I can't translate what the tools are telling me, can someone help?

From Knoppix I ran the following:
------------------------------------------------------------------------

root@Microknoppix:/home/knoppix# lvs
  /proc/misc: No entry for device-mapper found
  Is device-mapper driver missing from kernel?
  Failure to communicate with kernel device-mapper driver.
  /proc/misc: No entry for device-mapper found
  Is device-mapper driver missing from kernel?
  Failure to communicate with kernel device-mapper driver.
  Incompatible libdevmapper 1.02.27 (2008-06-25)(compat) and kernel driver 
  LV     VG   Attr   LSize Origin Snap%  Move Log Copy%  Convert
  root   svr  -wi--- 1.50T                                      
  swap_1 svr  -wi--- 7.19G                                      


root@Microknoppix:/home/knoppix# pvs
  PV         VG   Fmt  Attr PSize   PFree  
  /dev/sda1  svr  lvm2 a-   465.52G      0 
  /dev/sdb1  svr  lvm2 a-   465.76G      0 
  /dev/sdc1  svr  lvm2 a-   465.76G      0 
  /dev/sdd1  svr  lvm2 a-   465.76G 319.61G
  /dev/sde        lvm2 --     1.36T   1.36T


root@Microknoppix:/home/knoppix# vgs
  VG   #PV #LV #SN Attr   VSize VFree  
  svr    4   2   0 wz--n- 1.82T 319.61G


root@Microknoppix:/home/knoppix# vgdisplay
  --- Volume group ---
  VG Name               svr
  System ID             
  Format                lvm2
  Metadata Areas        4
  Metadata Sequence No  12
  VG Access             read/write
  VG Status             resizable
  MAX LV                0
  Cur LV                2
  /proc/misc: No entry for device-mapper found
  Is device-mapper driver missing from kernel?
  Failure to communicate with kernel device-mapper driver.
  /proc/misc: No entry for device-mapper found
  Is device-mapper driver missing from kernel?
  Failure to communicate with kernel device-mapper driver.
  Incompatible libdevmapper 1.02.27 (2008-06-25)(compat) and kernel driver 
  Open LV               0
  Max PV                0
  Cur PV                4
  Act PV                4
  VG Size               1.82 TB
  PE Size               4.00 MB
  Total PE              476875
  Alloc PE / Size       395056 / 1.51 TB
  Free  PE / Size       81819 / 319.61 GB
  VG UUID               wiSvTq-mCwo-n25G-GUkx-vvlr-5VV9-SjfTlg
   

root@Microknoppix:/home/knoppix# e2fsck -f /dev/svr/root
e2fsck 1.41.3 (12-Oct-2008)
e2fsck: No such file or directory while trying to open /dev/svr/root

The superblock could not be read or does not describe a correct ext2
filesystem.  If the device is valid and it really contains an ext2
filesystem (and not swap or ufs or something else), then the superblock
is corrupt, and you might try running e2fsck with an alternate superblock:
    e2fsck -b 8193 <device>

-------------------------------------------------------------------------

if the superblock is damaged as I reduced the VG too much what can I do.

It will not increae the VG as it tells me:
-----------------------------------------------------------
root@Microknoppix:/home/knoppix# lvextend /dev/svr/root -L +319.61G
  Rounding up size to full physical extent 319.61 GB
  Extending logical volume root to 1.81 TB
  Insufficient free space: 81821 extents needed, but only 81819 available
--------------------------------------------------------

any help would be much appreciated.

L

---

