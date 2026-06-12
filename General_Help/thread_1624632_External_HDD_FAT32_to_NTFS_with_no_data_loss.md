---
title: "External HDD FAT32 to NTFS with no data loss"
date: 2010-11-18
forum: General Help
---

### Post by travmanx on 2010-11-18
I have a 1TB External HD that at the time of purchasing was used with my PS3 which only allowed FAT32 HDs. But now I am using it for other uses. I have came across the problem of the file size limit of 4gb that FAT32 has.

The problem is I have about 200 GB filled of data on this HDD and wish to convert it to NTFS with no data being lossed. 

Is this possible and if so how?

Edit: BTW no Microsoft just Ubuntu

---

### Post by Mark Phelps on 2010-11-18
No one can guarantee against data loss any time you're messing with partitioning.  Something can always go wrong.

But since you have no access to MS Windows, I would recommend the following:
1) Attach the drive as an external to your Ubuntu PC
2) Open Partition Editor and select that drive
3) Shrink the FAT32 drive to half its size  -- be warned -- GParted is very S...L...O...W. This could take HOURS.
4) Create a new NTFS partition on that same drive using Partition Editor
5) Copy the files from the FAT32 partition to the NTFS partition
6) When done, safely remove the drive
7) Plugin the drive again and confirm that the files in the NTFS partition are OK
8) Using Partition Editor, remove the FAT32 partition.
9) Then, expand the NTFS partition to fill the drive.  Once again, be warned that GParted is S...L...O...W
10) Check the files again to be sure they are OK
11) Safely remove the drive

Using this approach, you don't mess with the original files until after you've confirmed that the copies are OK.

---

### Post by oldfred on 2010-11-18
+1 on Mark Phelps's suggestion.


But I am not sure with a 1TB drive I would only want one partition. Chkdsk will take forever. If you ever have system crash file recover will take forever and a day. Having some extra partitions helps organize things, but the disadvantage is that then you may not have planned ahead well and need to resize later.

---

