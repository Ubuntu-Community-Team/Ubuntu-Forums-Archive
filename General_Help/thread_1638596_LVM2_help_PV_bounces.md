---
title: "LVM2 help PV bounces??"
date: 2010-12-05
forum: General Help
---

### Post by jmcboots on 2010-12-05
Hello everyone, 

I have a really weird problem. It appears as if a physical volume is "bouncing" Using pvscan -v it will be there one minute and gone the next. The following is me just repeating a pvscan about once every second.

> root@finster:~# pvscan -v
    Wiping cache of LVM-capable devices
    Wiping internal VG cache
    Walking through all physical volumes
  /dev/md0: Checksum error
  PV /dev/md0                      lvm2 [1.36 TiB]
  Total: 1 [1.36 TiB] / in use: 0 [0   ] / in no VG: 1 [1.36 TiB]
root@finster:~# pvscan -v
    Wiping cache of LVM-capable devices
    Wiping internal VG cache
    Walking through all physical volumes
  No matching physical volumes found
root@finster:~# pvscan -v
    Wiping cache of LVM-capable devices
    Wiping internal VG cache
    Walking through all physical volumes
  Incorrect metadata area header checksum
  PV /dev/md0                      lvm2 [1.36 TiB]
  Total: 1 [1.36 TiB] / in use: 0 [0   ] / in no VG: 1 [1.36 TiB]
root@finster:~# pvscan -v
    Wiping cache of LVM-capable devices
    Wiping internal VG cache
    Walking through all physical volumes
  No matching physical volumes found
root@finster:~# pvscan -v
    Wiping cache of LVM-capable devices
    Wiping internal VG cache
    Walking through all physical volumes
  Incorrect metadata area header checksum
  PV /dev/md0                      lvm2 [1.36 TiB]
  Total: 1 [1.36 TiB] / in use: 0 [0   ] / in no VG: 1 [1.36 TiB]
root@finster:~# pvscan -v
    Wiping cache of LVM-capable devices
    Wiping internal VG cache
    Walking through all physical volumes
  No matching physical volumes found
root@finster:~# pvscan -v
    Wiping cache of LVM-capable devices
    Wiping internal VG cache
    Walking through all physical volumes
  No matching physical volumes found
root@finster:~# pvscan -v
    Wiping cache of LVM-capable devices
    Wiping internal VG cache
    Walking through all physical volumes
  No matching physical volumes found
root@finster:~# pvscan -v
    Wiping cache of LVM-capable devices
    Wiping internal VG cache
    Walking through all physical volumes
  Incorrect metadata area header checksum
  PV /dev/md0                      lvm2 [1.36 TiB]
  Total: 1 [1.36 TiB] / in use: 0 [0   ] / in no VG: 1 [1.36 TiB]


Here is what I have: 

I have two identical drives with /dev/sdb1 and /dev/sdb2 belonging to a raid array /dev/md0

> 
mdadm --detail /dev/md0
/dev/md0:
        Version : 00.90
  Creation Time : Thu Jul 23 09:11:18 2009
     Raid Level : raid1
     Array Size : 1465135936 (1397.26 GiB 1500.30 GB)
  Used Dev Size : 1465135936 (1397.26 GiB 1500.30 GB)
   Raid Devices : 2
  Total Devices : 2
Preferred Minor : 0
    Persistence : Superblock is persistent

    Update Time : Sun Dec  5 20:04:00 2010
          State : clean
 Active Devices : 2
Working Devices : 2
 Failed Devices : 0
  Spare Devices : 0

           UUID : 00238852:372485de:8b7a76cd:52aedffc
         Events : 0.2245321

    Number   Major   Minor   RaidDevice State
       0       8       17        0      active sync   /dev/sdb1
       1       8       33        1      active sync   /dev/sdc1


The array has an LVM2 filesystem on it with a vg of "homevg and and lv on that called "homelv" Very original, I know... 

The orginal computer the array was in was old and tired and finally gave up the ghost. I moved it to another machine, re assembled the array, and everything came right back on line after a little fiddling. 

The problems started with the LVM after a reboot. It appeared there was nothing in /dev/mapper for the LVM anymore and so I started trying to figure what went wrong.

lvdisplay had nothing
vgdisplay had nothing
and pvdisplay had nothing.

I went to recreate the pv from an archive file and then started getting all metadata error messages. Now it seems I cant remove or rebuild the pv. it just keeps appearing and then its gone, then appearing then gone. 

Now I am unable to vgcfgrestore because it says there is a problem with metadata checksums and errors out.

hopefully someone has an idea whats going on here.

Thanks in advance for your help!
john

---

### Post by jmcboots on 2010-12-06
Does anyone have any idea on this?

Is there an LVM2 guru in the house?

---

