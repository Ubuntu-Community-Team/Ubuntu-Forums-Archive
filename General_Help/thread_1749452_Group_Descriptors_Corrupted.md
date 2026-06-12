---
title: "Group Descriptors Corrupted"
date: 2011-05-04
forum: General Help
---

### Post by Delphinus369 on 2011-05-04
I cannot mount my RAID5 array because of corrupt group descriptors. I had to recover the RAID array because of a fault drive. The array says it recovered to 100% after the new drive was installed but now I can't mount the file system.

dmesg reports this error after I try to mount:

```

[97340.997516] RAID5 conf printout:
[97340.997517]  --- rd:8 wd:8
[97340.997518]  disk 0, o:1, dev:sdd
[97340.997520]  disk 1, o:1, dev:sde
[97340.997521]  disk 2, o:1, dev:sdf
[97340.997522]  disk 3, o:1, dev:sdh
[97340.997523]  disk 4, o:1, dev:sdi
[97340.997524]  disk 5, o:1, dev:sdj
[97340.997525]  disk 6, o:1, dev:sdk
[97340.997526]  disk 7, o:1, dev:sdg
[97340.997554] md1: detected capacity change from 0 to 14002791907328
[97340.997791]  md1: unknown partition table
[98964.428712] EXT3-fs error (device md1): ext3_check_descriptors: Block bitmap for group 8064 not in group (block 192442638)!
[98964.864883] EXT3-fs: group descriptors corrupted!
[99803.120684] VFS: Can't find ext3 filesystem on dev md1.
[99812.183909] EXT3-fs error (device md1): ext3_check_descriptors: Block bitmap for group 8064 not in group (block 192442638)!
[99812.620721] EXT3-fs: group descriptors corrupted!
[99815.736570] VFS: Can't find ext3 filesystem on dev md1.
[99931.385266] VFS: Can't find ext3 filesystem on dev md1.
[99943.455903] VFS: Can't find ext3 filesystem on dev md1.
[99963.458440] VFS: Can't find ext3 filesystem on dev md1.
[99984.715202] VFS: Can't find ext3 filesystem on dev md1.
[104455.509349] EXT3-fs error (device md1): ext3_check_descriptors: Block bitmap for group 8064 not in group (block 192442638)!
[104455.587657] EXT3-fs: group descriptors corrupted!
[106641.702551] EXT3-fs error (device md1): ext3_check_descriptors: Block bitmap for group 8064 not in group (block 192442638)!
[106642.159271] EXT3-fs: group descriptors corrupted!


```

Does anyone know how to recover the group descriptors?  I've tried to run fsck but it fails after a few minutes with a memory allocation error (this RAID array is 13TB).  I have about 6TB worth of data on the array that I would really, really, really like to recover and will be completely dejected if I lose all this data.

Thanks for the help. If there is anything else I can post to help further troubleshooting please let me know.

-Del

---

