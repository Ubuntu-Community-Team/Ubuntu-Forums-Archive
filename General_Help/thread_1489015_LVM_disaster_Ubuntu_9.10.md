---
title: "LVM disaster Ubuntu 9.10"
date: 2010-05-20
forum: General Help
---

### Post by metti81 on 2010-05-20
Hi,

I have setup a linear lvm Volume that somehow got broken after reboot (devices got renamed). I have managed to get the pvs, vgs and lvs back online but it seems the FS is broken:

[ 1932.929853] device-mapper: table: 252:2: linear: dm-linear: Device lookup failed
[ 1932.929866] device-mapper: ioctl: error adding target to table

  PV         VG    Fmt  Attr PSize   PFree   
  /dev/sdb1  vg001 lvm2 a-   931.51G 1008.00M
  /dev/sdc1  vg001 lvm2 a-   931.45G       0 

  VG    #PV #LV #SN Attr   VSize VFree   
  vg001   2   2   0 wz--n- 1.82T 1008.00M

 LV     VG    Attr   LSize   Origin Snap%  Move Log Copy%  Convert
  lv001  vg001 -wi-d-   1.82T                                      
  nsswap vg001 -wi-d- 512.00M     

I have the lvm meta data Backup but im not quite sure which uuid belongs to which drive. I may have messed it up already with trying to recreate the pvs and modifiying the partition tables on the disks.

Is there a possibility to recover the Data on the Drives?

---

### Post by metti81 on 2010-05-20
Ok got back access to the data, but the behavior is more than strange. I deleted the partition tables with:

dd if=/dev/zero of=/dev/sdX bs=512 count=1

In

dmsetup ls

there seems to be one device of the linear lvm (if fdisk the /dev/mapper device it shows a lvm partition) and blocking lvm access. If I remove the device via dmsetup, the lvm is online again. But after a reboot the logical volume is not mounted again. I would like to know where my mistake resides, right now i cannot not use any lvm related stuff. This adventure gave me a 4 hour nightmare before I got access back.
If u need more information i can provide more details.

---

