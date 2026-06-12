---
title: "cant run fsck from livecd - device or resource busy"
date: 2010-07-11
forum: General Help
---

### Post by mdgt on 2010-07-11
Hi,

My 10.04 (64) install has somehow managed to corrupt the fs - and im an now trying to rebuild it to get to some files that i really urgently need. 

However, even after I boot from a livecd, i get the following error:

```
$ fsck.ext4 -f /dev/sda1
fsck.ext4: Device or resource busy while trying to open /dev/sdb
Filesystem mounted or opened exclusively by another program?
```Even though this is def not the case - in fact, if i try to mount the drive, I get the following:

```
Error mounting: mount: wrong fs type, bad option, bad superblock on /dev/sdb1,
```It goes on to suggest I try the following log:

```
$ dmesg | tail 
[  163.182725] sr 4:0:0:0: [sr0] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[  163.182730] sr 4:0:0:0: [sr0] Sense Key : Illegal Request [current] 
[  163.182735] Info fld=0x576e3, ILI
[  163.182738] sr 4:0:0:0: [sr0] Add. Sense: Illegal mode for this track
[  163.182744] sr 4:0:0:0: [sr0] CDB: Read(10): 28 00 00 05 76 e3 00 00 01 00
[  163.182755] end_request: I/O error, dev sr0, sector 1432460
[  703.087819] EXT4-fs (sdb1): ext4_check_descriptors: Block bitmap for group 128 not in group (block 2553887680)!
[  703.087828] EXT4-fs (sdb1): group descriptors corrupted!
[ 1680.954774] EXT4-fs (sdb1): ext4_check_descriptors: Block bitmap for group 128 not in group (block 2553887680)!
[ 1680.954780] EXT4-fs (sdb1): group descriptors corrupted!

```
Any idea how i could force the fsck, i'm really in a bind here.. 

Many thanks!

---

### Post by tonystubblebine on 2010-12-22
I'm having a similar problem in 10.10. Were you able to resolve it?

I get the same "device or resource busy" error when trying to run fsck from a livecd. I even tried the Ubuntu rescue CD just in case there was something in the livecd that was accessing the drive.

---

### Post by contadinoste on 2011-01-30
Also it's an old topic: Probably fsck with Ubuntu 10.10 is bugged
[https://bugs.launchpad.net/ubuntu/+source/e2fsprogs/+bug/656526](https://bugs.launchpad.net/ubuntu/+source/e2fsprogs/+bug/656526)

So try do run  fsck  with another version: 10.04 or knoppix, archlinux ecc

---

