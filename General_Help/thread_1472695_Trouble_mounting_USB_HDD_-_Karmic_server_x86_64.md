---
title: "Trouble mounting USB HDD - Karmic server x86_64"
date: 2010-05-04
forum: General Help
---

### Post by Newpro on 2010-05-04
I have a 1TB HDD in a USB enclosure with a single partition formatted with NTFS.  Needless to say, I'm having trouble mounting the file system.  I will try to provide as much detail as I can, but I will be happy to add more upon request.

sudo mount /dev/sdb1 /mnt/cimsdv -t ntfs-3g

```
Error opening '/dev/sdb1': No such device or address
Failed to mount '/dev/sdb1': No such device or address
Either the device is missing or it's powered down, or you have
SoftRAID hardware and must use an activated, different device under
/dev/mapper/, (e.g. /dev/mapper/nvidia_eahaabcc1) to mount NTFS.
Please see the 'dmraid' documentation for help.
```sudo fdisk -l

```
Disk /dev/sda: 584.7 GB, 584652423168 bytes
255 heads, 63 sectors/track, 71079 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x0009d542

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       68198   547800403+  83  Linux
/dev/sda2           68199       71079    23141632+   5  Extended
/dev/sda5           68199       71079    23141601   82  Linux swap / Solaris

Disk /dev/sdb: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x54b94927

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1      121601   976760001    7  HPFS/NTFS
```dmesg | grep sdb

```
[507458.014094] sd 3:0:0:0: [sdb] 1953525168 512-byte logical blocks: (1.00 TB/931 GiB)
[507458.014819] sd 3:0:0:0: [sdb] Write Protect is off
[507458.014822] sd 3:0:0:0: [sdb] Mode Sense: 00 38 00 00
[507458.014825] sd 3:0:0:0: [sdb] Assuming drive cache: write through
[507458.016323] sd 3:0:0:0: [sdb] Assuming drive cache: write through
[507458.016327]  sdb: sdb1
[507458.034201] sd 3:0:0:0: [sdb] Assuming drive cache: write through
[507458.034205] sd 3:0:0:0: [sdb] Attached SCSI disk
[2478927.811548] sd 6:0:0:0: [sdb] 1953525168 512-byte logical blocks: (1.00 TB/931 GiB)
[2478927.812287] sd 6:0:0:0: [sdb] Write Protect is off
[2478927.812290] sd 6:0:0:0: [sdb] Mode Sense: 00 38 00 00
[2478927.812293] sd 6:0:0:0: [sdb] Assuming drive cache: write through
[2478927.814662] sd 6:0:0:0: [sdb] Assuming drive cache: write through
[2478927.814666]  sdb: sdb1
[2478927.827905] sd 6:0:0:0: [sdb] Assuming drive cache: write through
[2478927.827908] sd 6:0:0:0: [sdb] Attached SCSI disk
[2479153.151365] sd 7:0:0:0: [sdb] 1953525168 512-byte logical blocks: (1.00 TB/931 GiB)
[2479153.152322] sd 7:0:0:0: [sdb] Write Protect is off
[2479153.152326] sd 7:0:0:0: [sdb] Mode Sense: 00 38 00 00
[2479153.152329] sd 7:0:0:0: [sdb] Assuming drive cache: write through
[2479153.154105] sd 7:0:0:0: [sdb] Assuming drive cache: write through
[2479153.154109]  sdb: sdb1
[2479153.167606] sd 7:0:0:0: [sdb] Assuming drive cache: write through
[2479153.167610] sd 7:0:0:0: [sdb] Attached SCSI disk
[2479227.241427] sd 8:0:0:0: [sdb] 1953525168 512-byte logical blocks: (1.00 TB/931 GiB)
[2479227.242308] sd 8:0:0:0: [sdb] Write Protect is off
[2479227.242312] sd 8:0:0:0: [sdb] Mode Sense: 00 38 00 00
[2479227.242315] sd 8:0:0:0: [sdb] Assuming drive cache: write through
[2479227.243810] sd 8:0:0:0: [sdb] Assuming drive cache: write through
[2479227.243814]  sdb: sdb1
[2479227.252684] sd 8:0:0:0: [sdb] Assuming drive cache: write through
[2479227.252687] sd 8:0:0:0: [sdb] Attached SCSI disk
[2480141.961454] sd 9:0:0:0: [sdb] 1953525168 512-byte logical blocks: (1.00 TB/931 GiB)
[2480141.962641] sd 9:0:0:0: [sdb] Write Protect is off
[2480141.962646] sd 9:0:0:0: [sdb] Mode Sense: 00 38 00 00
[2480141.962652] sd 9:0:0:0: [sdb] Assuming drive cache: write through
[2480141.964449] sd 9:0:0:0: [sdb] Assuming drive cache: write through
[2480141.964454]  sdb: sdb1
[2480141.972953] sd 9:0:0:0: [sdb] Assuming drive cache: write through
[2480141.972957] sd 9:0:0:0: [sdb] Attached SCSI disk
[2484005.121413] sd 10:0:0:0: [sdb] 1953525168 512-byte logical blocks: (1.00 TB/931 GiB)
[2484005.122584] sd 10:0:0:0: [sdb] Write Protect is off
[2484005.122590] sd 10:0:0:0: [sdb] Mode Sense: 00 38 00 00
[2484005.122596] sd 10:0:0:0: [sdb] Assuming drive cache: write through
[2484005.124277] sd 10:0:0:0: [sdb] Assuming drive cache: write through
[2484005.124281]  sdb: sdb1
[2484005.140907] sd 10:0:0:0: [sdb] Assuming drive cache: write through
[2484005.140911] sd 10:0:0:0: [sdb] Attached SCSI disk
[2484420.652103] sd 11:0:0:0: [sdb] 1953525168 512-byte logical blocks: (1.00 TB/931 GiB)
[2484420.653343] sd 11:0:0:0: [sdb] Write Protect is off
[2484420.653350] sd 11:0:0:0: [sdb] Mode Sense: 00 38 00 00
[2484420.653355] sd 11:0:0:0: [sdb] Assuming drive cache: write through
[2484420.654860] sd 11:0:0:0: [sdb] Assuming drive cache: write through
[2484420.654864]  sdb: sdb1
[2484420.671109] sd 11:0:0:0: [sdb] Assuming drive cache: write through
[2484420.671113] sd 11:0:0:0: [sdb] Attached SCSI disk
[2499984.983386] sd 12:0:0:0: [sdb] 1953525168 512-byte logical blocks: (1.00 TB/931 GiB)
[2499984.985285] sd 12:0:0:0: [sdb] Write Protect is off
[2499984.985289] sd 12:0:0:0: [sdb] Mode Sense: 00 38 00 00
[2499984.985292] sd 12:0:0:0: [sdb] Assuming drive cache: write through
[2499984.986873] sd 12:0:0:0: [sdb] Assuming drive cache: write through
[2499984.986878]  sdb: sdb1
[2499985.005635] sd 12:0:0:0: [sdb] Assuming drive cache: write through
[2499985.005639] sd 12:0:0:0: [sdb] Attached SCSI disk
```

I will only be using this drive temporarily and have not added anything to fstab.

The drive works fine on my windoze server 2008.

I have no idea why this isn't working.  Any advice or direction would be greatly appreciated.

---

### Post by rnerwein on 2010-05-04
hi
you use: sudo mount /dev/sdb1 /mnt/cimsdv -t ntfs-3g
try:
sudo mount -t ntsf-3g /dev/sdb1 /mnt/cimsdv
or
sudo mount -t ntfs /dev/sdb1 /mnt/cimsdv
i guss you have already made a mountpoint /dev/cimsdv
ciao

---

### Post by Newpro on 2010-05-04
> hi
you use: sudo mount /dev/sdb1 /mnt/cimsdv -t ntfs-3g
try:
sudo mount -t ntsf-3g /dev/sdb1 /mnt/cimsdv
or
sudo mount -t ntfs /dev/sdb1 /mnt/cimsdv
i guss you have already made a mountpoint /dev/cimsdv
ciao 

Thanks for your reply.

I tried both variations and got the same results.

---

### Post by Newpro on 2010-05-05
Bump

---

### Post by Newpro on 2010-05-07
I've been reading for some time, trying to figure out why this isn't working.  Here is what I've done since the last post.

Plugged the drive into my windoze server and ran chkdsk /r.  It completed and did not find any errors.  Once complete, I made sure to properly stop the device using the "safely remove hardware" tool before unplugging.

Now when I plug my drive back into my ubuntu server, I see only /dev/sdb.  I do not see /dev/sdb1.   Strange, no?

sudo fdisk -l

```
Disk /dev/sda: 584.7 GB, 584652423168 bytes
255 heads, 63 sectors/track, 71079 cylinders, total 1141899264 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x0009d542

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          63  1095600869   547800403+  83  Linux
/dev/sda2      1095600870  1141884134    23141632+   5  Extended
/dev/sda5      1095600933  1141884134    23141601   82  Linux swap / Solaris

Disk /dev/sdb: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x54b94927

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1              63  1953520064   976760001    7  HPFS/NTFS
```

Here we have sdb1, but not in the file system.

mount -t ntfs-3g /dev/sdb1 /mnt/usbhdd     <--- changed mount point to me more descriptive.

```
ntfs-3g: Failed to access volume '/dev/sdb1': No such file or directory

ntfs-3g 2009.4.4 external FUSE 27 - Third Generation NTFS Driver

Copyright (C) 2005-2007 Yura Pakhuchiy
Copyright (C) 2006-2009 Szabolcs Szakacsits
Copyright (C) 2007-2009 Jean-Pierre Andre
Copyright (C) 2009 Erik Larsson

Usage:    ntfs-3g [-o option[,...]] <device|image_file> <mount_point>

Options:  ro (read-only mount), remove_hiberfile, uid=, gid=,
          umask=, fmask=, dmask=, streams_interface=, syncio.
          Please see the details in the manual (type: man ntfs-3g).

Example: ntfs-3g /dev/sda1 /mnt/windows

Ntfs-3g news, support and information:  http://ntfs-3g.org
```

No surprise here; /dev/sdb1 does not exist.

sudo dmesg | tail

```
[3088246.960286] scsi 14:0:0:0: Direct-Access     WDC WD10 01FALS-00E3A0    1D05 PQ: 0 ANSI: 2 CCS
[3088246.960893] sd 14:0:0:0: Attached scsi generic sg3 type 0
[3088246.961515] sd 14:0:0:0: [sdb] 1953525168 512-byte logical blocks: (1.00 TB/931 GiB)
[3088246.962271] sd 14:0:0:0: [sdb] Write Protect is off
[3088246.962274] sd 14:0:0:0: [sdb] Mode Sense: 00 38 00 00
[3088246.962277] sd 14:0:0:0: [sdb] Assuming drive cache: write through
[3088246.964510] sd 14:0:0:0: [sdb] Assuming drive cache: write through
[3088246.964514]  sdb: sdb1
[3088246.980141] sd 14:0:0:0: [sdb] Assuming drive cache: write through
[3088246.980145] sd 14:0:0:0: [sdb] Attached SCSI disk

```

I chose ubuntu because of the great support community.  Don't let me down.

---

### Post by Newpro on 2010-05-07
A note to others with this problem:

Don't waste anymore time with this.  Just plug your drive into a Windows box and mount the share.

That's right, I said it.

Good day, sirs/ma'ams.

---

