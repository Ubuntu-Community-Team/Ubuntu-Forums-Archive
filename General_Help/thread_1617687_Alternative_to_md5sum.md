---
title: "Alternative to md5sum"
date: 2010-11-09
forum: General Help
---

### Post by ianc1 on 2010-11-09
I was about to write a Python routine to recursively copy a given directory to a destination directory and check the checksums (md5sum) of the files to confirm correct copies.  Clearly to do this requires a list of checksums prior to the task which I will also include in the routine.

The code I use to generate the checksum list is:
```
find *DIRECTORY* -type f -print0 | xargs -0 md5sum > ./*DIRECTORY_NAME*.md5
```Now for 12 GB this took about 10 mins.  I appreciate the time is dependent on the quantity of files.  But if I were to back up my TB drive using this procedure I may never get access to the PC again as this would be seriously lengthy.

Is there an alternative approach to this that may be faster.  I know of the diff function but as far as I am aware that tells me of files missing not whether they copied correctly.

Thanks

---

### Post by Dave_L on 2010-11-09
If the source and destination are each in a Linux file system, I think the *rsync* shell command is a much more efficient choice than a Python script.  And rsync includes verification, so you wouldn't need to do separate MD5-ing.

---

### Post by ianc1 on 2010-11-09
Thanks.  I'll look into rsync.  The reason for choosing a Pyhton script was to learn a little more Python; it's something I've started using recently mainly for data analysis and GUIs with Qt.  I have yet to use it to run bash commands though so this was to be my first use.  However rsync sounds worth looking into.

I presume the speed or lack of could still be an issue if it does md5sums on hundreds or thousands of files.

Thanks again.

---

