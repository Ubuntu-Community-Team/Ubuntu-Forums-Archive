---
title: "Linux Boot Disk Format procedure problem"
date: 2011-07-02
forum: General Help
---

### Post by Jim Pan on 2011-07-02
I am working on Ubuntu 11.04 for Beagleboard. I am not sure this is the right place to post this question.

I followed the procedure to set the two partitions and tried to format the partitions. (mkfs,msdod, mkfs.ext3)
I thought by putting the Command (m for help): [w]  The partition table was changed from  W95 FAT32 (LBA) to
a totally different list.
[t]  used to be [c] W95 FAT32 (LBA) now they are

0 unassigned   4 SunOS usr    8 SunOS home    82 Linux swap
1 Boot            5 Whole disk    9 SunOS alt secto  83 Linux native
2 SunOS root  .....
3 SunOS swap .....

Please let me know how to go back to the original W95 FAT32 (LBA).

Thanks,
Jim

---

