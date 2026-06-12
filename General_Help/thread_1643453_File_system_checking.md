---
title: "File system checking"
date: 2010-12-11
forum: General Help
---

### Post by nPn_ on 2010-12-11
Is running fsck -f sufficient to ensure my data is OK? 

Heres what's happened

My system crashed during a gparted operation.  I was pretty sure however, that the data was OK since given the size of the drive and the amount of data and were it was when it crashed, I figured  the crash occurred while moving empty space.

Bottom line is I think the data is OK, but I am wondering what else I can do to check it.

When I first ran fsck after re-booting the system it said it was clean.  I then did fsck -f and it found and fixed errors in phase 5 (group summary).  Now when I run fsck -f I think it's clean?

fsck from util-linux-ng 2.17.2
e2fsck 1.41.12 (17-May-2010)
Pass 1: Checking inodes, blocks, and sizes
Pass 2: Checking directory structure
Pass 3: Checking directory connectivity
Pass 4: Checking reference counts
Pass 5: Checking group summary information
office-shares: 113666/52199424 files (1.2% non-contiguous), 80922816/208784384 blocks


The concern I have is that I was having lots of issues even booting for a while.  I think I found the reason for that (I had not used a screw to hold in the video card and it was becoming partially dislodged)

Is there anything else I should do to check the data?  It _seems_ like it is all there and I think the above message means that fsck thinks it is OK also.

Thanks - nPn

---

### Post by dcstar on 2010-12-12
> **nPn_ said:**
> **Is running fsck -f sufficient to ensure my data is OK**? 
..........
**Is there anything else I should do to check the data?**  It _seems_ like it is all there and I think the above message means that fsck thinks it is OK also.


[LIST=1]
[*]Yes.
[*]No.
[/LIST]

---

### Post by nPn_ on 2010-12-12
thanks!

---

### Post by rickyrockrat on 2010-12-12
fsck only checks the file system integrity, not data integrity.  It is difficult to do data validation, and since fsck fixed some errors, it is possible you lost some data.  Do you have a disk clone or some way to validate the data?  You *did* backup before you tried parted?

Do you have detailed errors from that fsck?

---

### Post by nPn_ on 2010-12-23
Thanks rickyrockrat,  I don't have any more details on the error messages and I don't have a "backup" of the data as the data is pretty much backups of data on windows machine (clonezilla images and ms synctoy backups).  

Since all of the pc's are still healthy I will re-snapshot them over the next week or so,  unless there is some way to check the integrity of a clonezilla image? 

For the synctoy stuff I found an interesting option that I will turn on (at least for 1 cycle).  You can have it "check file contents",  which means it will compare the SHA1 hash of both files to determine if the file needs to be copied or not.  It will be interesting to see if there are any mis-compares.

nPn

---

