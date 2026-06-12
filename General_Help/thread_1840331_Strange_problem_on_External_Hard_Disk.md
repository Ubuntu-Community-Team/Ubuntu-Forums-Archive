---
title: "Strange problem on External Hard Disk"
date: 2011-09-07
forum: General Help
---

### Post by maglev on 2011-09-07
I have Ubuntu 10.04 (32 bit) installed on my AMD Phenom II X4 desktop.

I have used my 2 TB Planex external hard disk without any problem until several days ago.
After copying files to and from the hard disk,
any program suddenly could not write to the disk,
but strangely still can read any files in the hard disk.

When I tried to create new folder or rename files,
there's errors :
```

Error creating directory: Input/output error
Error renaming file: Input/output error
```When I thought I couldn't write to the hard disk at all,
strangely I could create folder or rename files on the folders with depth 2
(e.g., I could modify the files in the /REMOVABLE_DISK/FOLDER/FOLDER/,
but can not modify the contents of /REMOVABLE_DISK/FOLDER/.
Here /REMOVABLE_DISK/ is the root directory of external hard disk)

I have been searching around,
including using **ntfsfix**, but still no luck.
I also had tried to plug the hdd on my vista,
but vista could not access the hard disk at all,
although it seems it could recognize it as removable hard disk.

When I trying to manually mount the disk in my ubuntu,
I got following errors (but still could mounted it succesfully)
```
Incomplete multi-sector transfer: magic: 0x58444e49  size: 4096  usa_ofs: 40  usa_count: 6  data: 52845  usn: 52844: Input/output error
Incomplete multi-sector transfer: magic: 0x58444e49  size: 4096  usa_ofs: 40  usa_count: 6  data: 52845  usn: 52844: Input/output error
Incomplete multi-sector transfer: magic: 0x58444e49  size: 4096  usa_ofs: 40  usa_count: 6  data: 52845  usn: 52844: Input/output error
Incomplete multi-sector transfer: magic: 0x58444e49  size: 4096  usa_ofs: 40  usa_count: 6  data: 52845  usn: 52844: Input/output error

```The good thing is,
I still can access(read) any files in my ubuntu,
but I need to create folder etc.

Any help will be very appreciate.

---

### Post by maglev on 2011-09-07
I found the answer here :[http://ubuntuforums.org/showthread.php?p=10681424](http://ubuntuforums.org/showthread.php?p=10681424)

Just run
```
chkdsk E: /f
```on windows, and it will repair some broken files(?).

---

