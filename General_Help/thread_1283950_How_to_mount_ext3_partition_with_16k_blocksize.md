---
title: "How to mount ext3 partition with 16k blocksize?"
date: 2009-10-06
forum: General Help
---

### Post by EddieX on 2009-10-06
Hi,

I have a disk that contains a LVM2-volume which has been created by my ReadyNAS, and I want to access the data by mounting the disk manually by hooking it up to my workstation.

It seems that the ReadyNAS has created a Ext3 partition with a blocksize of 16k, which gives me the following error when I try to mount it:
```
EXT3-fs: bad blocksize 16384
```

pvscan gives:
```

  PV /dev/sdb5   VG c   lvm2 [463,53 GB / 0    free]
  Total: 1 [463,53 GB] / in use: 1 [463,53 GB] / in no VG: 0 [0   ]

```

lvscan gives:
```

ACTIVE            '/dev/c/c' [463,53 GB] inherit

```

tune2fs -l on the logical volume (/dev/c/c) gives:
```

tune2fs 1.41.4 (27-Jan-2009)
Filesystem volume name:   c
Last mounted on:          <not available>
Filesystem UUID:          71df24e7-a61e-4685-a9b8-b5f8377bd6a3
Filesystem magic number:  0xEF53
Filesystem revision #:    1 (dynamic)
Filesystem features:      has_journal resize_inode dir_index filetype
needs_recovery sparse_super large_file
Filesystem flags:         signed_directory_hash 
Default mount options:    (none)
Filesystem state:         clean
Errors behavior:          Continue
Filesystem OS type:       Linux
Inode count:              15204352
Block count:              30377984
Reserved block count:     0
Free blocks:              30223788
Free inodes:              15204327
First block:              0
Block size:               16384
Fragment size:            16384
Reserved GDT blocks:      128
Blocks per group:         65528
Fragments per group:      65528
Inodes per group:         32768
Inode blocks per group:   256
Filesystem created:       Mon Oct  5 08:55:09 2009
Last mount time:          Mon Oct  5 14:36:47 2009
Last write time:          Mon Oct  5 14:36:47 2009
Mount count:              6
Maximum mount count:      -1
Last checked:             Mon Oct  5 08:55:09 2009
Check interval:           0 (<none>)
Reserved blocks uid:      0 (user root)
Reserved blocks gid:      0 (group root)
First inode:              11
Inode size:	          128
Journal inode:            8
Default directory hash:   tea
Directory Hash Seed:      e3c673bd-9347-865f-4923-fb8e931660a7
Journal backup:           inode blocks

```

Is there a way to mount this partition with a blocksize of 16k ?

Thanks in advance!

Best regards,
Eddie

---

### Post by bogdan.veringioiu on 2009-10-06
Hi.
I am not sure how to mount 16k blocksize ext3 partitions, but I am under the impresion that this is a limitation from the kernel..
[http://lwn.net/Articles/188382/](http://lwn.net/Articles/188382/)
I think the default size is 4k.
Try to recreate your partition with 4k block size, then mount it.
Cheers.
Bogdan

---

