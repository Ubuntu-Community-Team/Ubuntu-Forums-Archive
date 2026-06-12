---
title: "Internal Hard Drive fails to mount."
date: 2010-02-14
forum: General Help
---

### Post by beastrace91 on 2010-02-14
Howdy All,

So when I booted my system up today my second internal hard drive which is formatted to ext4 failed to auto-mount for me(I have an fstab entry for it). When I I tried to manually mount it from terminal it failed and suggested I run **dmesg | tail** and here is the output from said command: ```
dmesg | tail
[  292.424199] sd 2:0:0:0: [sdb] Result: hostbyte=DID_BAD_TARGET driverbyte=DRIVER_OK
[  292.424208] end_request: I/O error, dev sdb, sector 65
[  292.424456] EXT4-fs (sdb1): unable to read superblock
[  298.348591] DRS: unkown mode,default use 11N 1S AP 
[  298.348602] DRS: unkown mode (SupRateLen=8, ExtRateLen=4, MCSSet[0]=0x0, MCSSet[1]=0x0)
[  301.371878] ===>rt_ioctl_giwscan. 1(1) BSS returned, data->length = 80
[  306.211535] sd 2:0:0:0: [sdb] Unhandled error code
[  306.211543] sd 2:0:0:0: [sdb] Result: hostbyte=DID_BAD_TARGET driverbyte=DRIVER_OK
[  306.211552] end_request: I/O error, dev sdb, sector 65
[  306.211581] EXT4-fs (sdb1): unable to read superblock

```

What happened exactly and how can I fix it?...

Regards,
~Jeff

---

### Post by Satoru-san on 2010-02-14
Not an ubuntu problem, not any thing to do with the os, the drive is simply bad, if it has important data on it you might want to throw it in the freezer for a short time then try to mount it and get your files off of it and get a new one. It might also be the IDE or SATA cable.

---

### Post by sandyd on 2010-02-14
> **beastrace91 said:**
> Howdy All,

So when I booted my system up today my second internal hard drive which is formatted to ext4 failed to auto-mount for me(I have an fstab entry for it). When I I tried to manually mount it from terminal it failed and suggested I run **dmesg | tail** and here is the output from said command: ```
dmesg | tail
[  292.424199] sd 2:0:0:0: [sdb] Result: hostbyte=DID_BAD_TARGET driverbyte=DRIVER_OK
[  292.424208] end_request: I/O error, dev sdb, sector 65
[  292.424456] EXT4-fs (sdb1): unable to read superblock
[  298.348591] DRS: unkown mode,default use 11N 1S AP 
[  298.348602] DRS: unkown mode (SupRateLen=8, ExtRateLen=4, MCSSet[0]=0x0, MCSSet[1]=0x0)
[  301.371878] ===>rt_ioctl_giwscan. 1(1) BSS returned, data->length = 80
[  306.211535] sd 2:0:0:0: [sdb] Unhandled error code
[  306.211543] sd 2:0:0:0: [sdb] Result: hostbyte=DID_BAD_TARGET driverbyte=DRIVER_OK
[  306.211552] end_request: I/O error, dev sdb, sector 65
[  306.211581] EXT4-fs (sdb1): unable to read superblock

```

What happened exactly and how can I fix it?...

Regards,
~Jeff
try
```

sudo fsck -y /dev/sdaxx

```
replace /dev/sdaxx with your drive
it looks like the ext4 journal superblock is corrupt

---

### Post by beastrace91 on 2010-02-14
> **carlee said:**
> try
```

sudo fdisk -y /dev/sdaxx

```
replace /dev/sdaxx with your drive
it looks like the ext4 journal superblock is corrupt

Invalid argument **-y** ```
oem@mintmedia ~ $ sudo fdisk -y /dev/sdb1
fdisk: invalid option -- 'y'

Usage: fdisk [-b SSZ] [-u] DISK     Change partition table
       fdisk -l [-b SSZ] [-u] DISK  List partition table(s)
       fdisk -s PARTITION           Give partition size(s) in blocks
       fdisk -v                     Give fdisk version
Here DISK is something like /dev/hdb or /dev/sda
and PARTITION is something like /dev/hda7
-u: give Start and End in sector (instead of cylinder) units
-b 2048: (for certain MO disks) use 2048-byte sectors

```

I've heard of freezing drives before, do I let it thaw before connecting it into my computer or take it out and plug it right in cold?

~Jeff

---

### Post by sandyd on 2010-02-14
> **beastrace91 said:**
> Invalid argument **-y** ```
oem@mintmedia ~ $ sudo fdisk -y /dev/sdb1
fdisk: invalid option -- 'y'

Usage: fdisk [-b SSZ] [-u] DISK     Change partition table
       fdisk -l [-b SSZ] [-u] DISK  List partition table(s)
       fdisk -s PARTITION           Give partition size(s) in blocks
       fdisk -v                     Give fdisk version
Here DISK is something like /dev/hdb or /dev/sda
and PARTITION is something like /dev/hda7
-u: give Start and End in sector (instead of cylinder) units
-b 2048: (for certain MO disks) use 2048-byte sectors

```

I've heard of freezing drives before, do I let it thaw before connecting it into my computer or take it out and plug it right in cold?

~Jeff

im terrible. huge typo. fixed.

---

### Post by Satoru-san on 2010-02-14
> **carlee said:**
> im terrible. huge typo. fixed.
He didn't type it wrong, there is no Y option in fdisk.

---

### Post by sandyd on 2010-02-14
> **Satoru-san said:**
> He didn't type it wrong, there is no Y option in fdisk.

i meant I made a huge typo

---

### Post by beastrace91 on 2010-02-14
> **Satoru-san said:**
> He didn't type it wrong, there is no Y option in fdisk.

:( Guess the ice box it is... Heres to hoping I can recover at least SOME of my 800gigs from it.

~Jeff

---

