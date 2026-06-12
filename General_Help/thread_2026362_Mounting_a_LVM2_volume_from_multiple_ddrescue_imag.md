---
title: "Mounting a LVM2 volume from multiple ddrescue images"
date: 2012-07-15
forum: General Help
---

### Post by psatyshur on 2012-07-15
Hi,

I am having an unusual problem (I think). I have been tasked with recovering data from a bunch of old hard drives. Most of them are pretty easy (the drives are in pretty good shape), but I am having a problem with a particular set.

My process is:
[LIST]
[*]Connect the drive
[*]Boot into Ubuntu
[*]Run ddrescue
[*]Disconnect the drive
[*]Mount the image and copy off any important files
[/LIST]

The problem drives were (apparently) part of a LVM2 volume. I have imaged both drives without problems, but I can't mount them. I am using a slightly modified method to the one outlined [here]("http://www.thegibson.org/blog/archives/467").

First, I find the offset for the start of the LVM partition using mmls
```
$ mmls wd_160gb_1.img
DOS Partition Table
Offset Sector: 0
Units are in 512-byte sectors

     Slot    Start        End          Length       Description
00:  Meta    0000000000   0000000000   0000000001   Primary Table (#0)
01:  -----   0000000000   0000000062   0000000063   Unallocated
02:  00:00   0000000063   0000208844   0000208782   Linux (0x83)
03:  00:01   0000208845   0312576704   0312367860   Linux Logical Volume Manager (0x8e)
04:  -----   0312576705   0312581807   0000005103   Unallocated

```

and

```
$ mmls ibm_32gb.img
DOS Partition Table
Offset Sector: 0
Units are in 512-byte sectors

     Slot    Start        End          Length       Description
00:  Meta    0000000000   0000000000   0000000001   Primary Table (#0)
01:  -----   0000000000   0000000062   0000000063   Unallocated
02:  00:00   0000000063   0060034904   0060034842   Linux Logical Volume Manager (0x8e)
03:  -----   0060034905   0060036479   0000001575   Unallocated

```

From this, the offset for the partitions I want are 63 for the IBM, and 208845 for the WD. The numbers have to be multiplied by the block size (512). I then create loopback devices for the two drives.

```
$ sudo losetup /dev/loop0 wd_160gb_1.img -o106928640
```

and

```
$ sudo losetup /dev/loop1 ibm_32gb.img -o32256
```

I then have LVM scan for the drives.

```
$ sudo lvm pvscan
  PV /dev/loop0   VG VolGroup00   lvm2 [148.94 GiB / 0    free]
  PV /dev/loop1   VG VolGroup00   lvm2 [28.62 GiB / 64.00 MiB free]
  Total: 2 [177.56 GiB] / in use: 2 [177.56 GiB] / in no VG: 0 [0   ]

```

Next, we activate the group:

```
$ sudo lvm vgchange -ay
  2 logical volume(s) in volume group "VolGroup00" now active

```

Finally, we list the logical volumes.

```
$ sudo lvm lvs
  LV       VG         Attr   LSize   Origin Snap%  Move Log Copy%  Convert
  LogVol00 VolGroup00 -wi-a- 176.50g
  LogVol01 VolGroup00 -wi-a-   1.00g

```

At this point, a few new devices show up in /dev

```
$ cd /dev/VolGroup00
$ ls
LogVol00  LogVol01

```

My next plan was to mount the volume LogVol00. This is where the trouble arises:

```
$ sudo mount /dev/VolGroup00/LogVol00 /mnt -o ro,user
mount: you must specify the filesystem type

```

I feel I may be missing something easy, but being a linux noob, I cant figure out what it might be. I was under the impression that 'mount' would try to figure out what the file system was for the partition. I doubt the file system is too obscure, so I expected that mount would be able to ID it. Any suggestions?

In case it matters:
```
$ uname -a
Linux Vault 3.2.0-26-generic #41-Ubuntu SMP Thu Jun 14 17:49:24 UTC 2012 x86_64 x86_64 x86_64 GNU/Linux
$ lsb_release -a
No LSB modules are available.
Distributor ID: Ubuntu
Description:    Ubuntu 12.04 LTS
Release:        12.04
Codename:       precise

```

Thanks.

---

### Post by psatyshur on 2012-07-15
No suggestions? I know this is not a problem with Ubuntu specifically, is there a better place to ask this kind of question?

---

### Post by steeldriver on 2012-07-15
have you tried

```
sudo file -s /dev/VolGroup00/LogVol00
```to find the filesystem type?

---

### Post by psatyshur on 2012-07-15
Here is the output

```
$ sudo file -s /dev/VolGroup00/LogVol00
/dev/VolGroup00/LogVol00: symbolic link to `../dm-0'

$ sudo file -s /dev/dm-0
/dev/dm-0: data

$ sudo mount /dev/dm-0 /mnt -o ro,user
mount: you must specify the filesystem type
```

That doesn't look promising. Could it be an encrypted volume? Do I need to download definitions for other file system types?

---

### Post by steeldriver on 2012-07-15
That's a good question - I don't know - sorry for forgetting about the symlink as well

One type that is sometimes used for large volumes is xfs, and iirc that doesn't have things like mkfs installed by default - I guess there's no harm in doing

```
sudo apt-get install xfsprogs xfsdump
```and then trying again - FWIW here's what I get for an ext4 and an xfs lvm:

```
$ sudo file -s /dev/dm-1
/dev/dm-1: Linux rev 1.0 ext4 filesystem data, UUID=bb5c5da2-4c75-4212-ad1d-1f4b691c7d76 (needs journal recovery) (extents) (large files) (huge files)

``````
$ sudo file -s /dev/dm-3
/dev/dm-3: SGI XFS filesystem data (blksz 4096, inosz 256, v2 dirs)
```

---

### Post by psatyshur on 2012-07-16
> **steeldriver said:**
> One type that is sometimes used for large volumes is xfs, and iirc that doesn't have things like mkfs installed by default - I guess there's no harm in doing

I installed XFS and got the same result. The file system on these drives shouldn't be anything too strange. Perhaps I am mounting the drives incorrectly? I sort of assumed that if the lvm could be found and activated, that the drives were setup correctly. However, this may not be the case.

---

### Post by steeldriver on 2012-07-16
well it's odd that 'file -s' can't determine the filetype - and I don't know if mount will work without it - but fwiw I *do* seem to remember there's something odd about mounting the lvm volumes - iirc I had to use 

EITHER

1. the symlink at /dev/mapper (in my case that's /dev/mapper/vg0-lv0 ; yours is probably /dev/mapper/VolGroup00-LogVol00) NOT the symlink at /dev/VolGroup00/LogVol00 (even though they both point to the same /dev/dm-N device)

OR

2. the corresponding UUID from 'sudo blkid /dev/mapper/VolGroup00-LogVol00' (note that this does NOT seem to be the same as the 'LV UUID' given by lvdisplay)

So maybe try

```
sudo mount  -o ro /dev/mapper/VolGroup00-LogVol00 /mnt
```and if that still complains about fstype I'd just try a bunch - ext2, ext3, ext4 etc.

```
sudo mount  -t ext2 -o ro /dev/mapper/VolGroup00-LogVol00 /mnt
```EDIT: you could also try 'parted' to probe the fstype - this seems to work on my lvms (using EITHER the /dev/mapper/vgXX-lvXX or /dev/vgXX/lvXX symlinks):

```
 sudo parted /dev/mapper/VolGroup00-LogVol00 print
```Beyond that I'm out of ideas...

---

