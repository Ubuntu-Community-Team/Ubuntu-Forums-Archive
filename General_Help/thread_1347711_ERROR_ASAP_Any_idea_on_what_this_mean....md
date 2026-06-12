---
title: "ERROR ASAP: Any idea on what this mean..."
date: 2009-12-06
forum: General Help
---

### Post by jk.cheng on 2009-12-06
root@jk-cheng-laptop:~# fsck.vfat -l /dev/sdb1
dosfsck 3.0.3, 18 May 2009, FAT32, LFN
Checking file /
Checking file /.Trash-1000 (TRASH-~1)
Checking file /Library (LIBRARY)
Checking file /Applications (APPLIC~1)
Checking file /Documents (DOCUME~1)
Checking file /Music (MUSIC)
Checking file /Pictures (PICTURES)
Checking file /Sites (SITES)
Checking file /2009-10-25-oo (2009-1~2)
Checking file /Videos (VIDEOS)
Checking file /FSCK0000.REC
Wrong checksum for long file name "2009-12-06".
  (Short name FSCK0001.REC may have changed without updating the long name)
1: Delete LFN
2: Leave it as it is.
3: Fix checksum (attaches to short name FSCK0001.REC)
? 

REMARK: The files in that directory is important. So, which 1 should i choose???

---

