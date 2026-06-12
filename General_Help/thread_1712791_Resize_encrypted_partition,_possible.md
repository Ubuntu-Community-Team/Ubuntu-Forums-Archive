---
title: "Resize encrypted partition, possible?"
date: 2011-03-23
forum: General Help
---

### Post by fackamato on 2011-03-23
Edit: just found this: [How to Resize a LUKS Encrypted File System.](http://ubuntuforums.org/showthread.php?p=4530641)

Hi,

I'm running Ubuntu 10.10 and it's installed with the default encryption scheme. The partition layout looks like this:

```
Disk /dev/sda: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00042e60

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1          32      248832   83  Linux
Partition 1 does not end on cylinder boundary.
/dev/sda2              32       38914   312320001    5  Extended
/dev/sda5              32       38914   312320000   83  Linux

```

sda5 is the encrypted partition, which I want to shrink (to 50GB or so):

```
cryptsetup -v luksDump  /dev/sda5
LUKS header information for /dev/sda5

Version:       	1
Cipher name:   	aes
Cipher mode:   	cbc-essiv:sha256
Hash spec:     	sha1
Payload offset:	2056
MK bits:       	256
MK digest:     	37 35 01 fb c3 08 10 93 a7 3d 0c 6a e0 7a d1 8c e5 2d 3a cf 
MK salt:       	6e b2 62 ca 36 11 e6 32 a0 8a ba 3b e5 88 e7 bc 
               	4e 50 17 50 86 82 73 f6 03 02 9f a4 c4 48 31 1d 
MK iterations: 	44875
UUID:          	1df0def9-bfe0-4918-9d21-3ed1494d14c0

Key Slot 0: ENABLED
	Iterations:         	179996
	Salt:               	70 1e b5 5a f4 66 29 70 6e 6c 56 88 19 f9 7e 1d 
	                      	1d ee d4 40 a0 9c 40 e5 65 94 a3 b4 64 91 5f 88 
	Key material offset:	8
	AF stripes:            	4000
Key Slot 1: DISABLED
Key Slot 2: DISABLED
Key Slot 3: DISABLED
Key Slot 4: DISABLED
Key Slot 5: DISABLED
Key Slot 6: DISABLED
Key Slot 7: DISABLED
Command successful.

```

Ubuntu uses LVM on top of that, like so:

```
$ ls -l /dev/mapper/
total 0
lrwxrwxrwx 1 root root       7 2011-03-23 09:34 root -> ../dm-1
crw------- 1 root root 10, 236 2011-03-23 08:23 control
lrwxrwxrwx 1 root root       7 2011-03-23 08:23 sdb5_crypt -> ../dm-0

$ pvdisplay
  --- Physical volume ---
  PV Name               /dev/dm-0
  VG Name               root
  PV Size               297.85 GiB / not usable 3.00 MiB
  Allocatable           yes 
  PE Size               4.00 MiB
  Total PE              76249
  Free PE               2754
  Allocated PE          73495
  PV UUID               5QHYaR-6Ygw-NfPB-ot2U-dKvw-h2aZ-xM4lgI
```

Then an ext4 partition on top of the logical volume in LVM.

My question is, can I shrink the encrypted partition? If so, is it enough to do this:

1) Shrink the ext4 file system to the desired size, or just below it.
2) Shrink the LVM logical volume, but make sure it's not smaller than the ext4 file system.
3) Shrink the LVM physical volume to the smallest possible size.
4) Shrink the LUKS "container" somehow.
5) Finally delete the sda5 partition.
6) Re-create the sda5 partition starting at the same sector, and make it ~50GB in size.
7) Profit???


Thanks,

---

### Post by klikevil on 2011-05-05
why was this marked solved if there is no answer? lol

---

