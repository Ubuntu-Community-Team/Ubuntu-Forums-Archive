---
title: "GParted error - drive partition now &quot;unknown&quot;"
date: 2011-08-06
forum: General Help
---

### Post by CluelessWinboxUser on 2011-08-06
Hi all,

I tried today to rezise a 3 TB drive and ended up with the following error:

-----
shrink file system  00:12:43    ( ERROR )
        
resize2fs /dev/sdb1 2046975982K
        
Resizing the filesystem on /dev/sdb1 to 511743995 (4k) blocks.
resize2fs 1.41.12 (17-May-2010)
resize2fs: Attempt to read block from filesystem resulted in short read while trying to resize /dev/sdb1
Please run 'e2fsck -fy /dev/sdb1' to fix the filesystem
after the aborted resize operation.
check file system on /dev/sdb1 for errors and (if possible) fix them  00:00:00    ( ERROR )
        
e2fsck -f -y -v /dev/sdb1
        
Could this be a zero-length partition?
e2fsck 1.41.12 (17-May-2010)
e2fsck: Attempt to read block from filesystem resulted in short read while trying to open /dev/sdb1
-----

Unfortunately the drive seems to be corrupted now, Ubuntu's disc utility says "unkonwn". Is there any chance I could regain access to the files that were on the disk? It was originally in ext4.

Thanks for any feedback.

---

### Post by Quackers on 2011-08-06
Have you tried to run ```
e2fsck -fy /dev/sdb1
``` as the output suggests? What happened?

---

### Post by CluelessWinboxUser on 2011-08-06
It gave me this error:
e2fsck: Attempt to read block from filesystem resulted in short read while trying to open /dev/sdb1

So I decided to just do a reboot. That solved all issues. The drive suddenly was readable again without any issues. This looks a lot like the HDD is dying slowly. I will copy all data off it and Run the Hitachi drive test to see what the heck is going on.

Thanks for the feedback.

---

### Post by jayadeep on 2011-08-06
please try to do that with partitionmanager...

---

