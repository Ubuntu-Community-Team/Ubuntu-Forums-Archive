---
title: "Partition full, but not full?"
date: 2009-07-24
forum: General Help
---

### Post by candtalan on 2009-07-24
I use ubuntu 8.04 in a 50GB partition, and also have ubuntu 9.04 in another partition, so I can run either.
I keep data on a separate disc so the 8.04 partition should not get full.
However, this morning I notice that when I open nautilus it reports almost no free space although I can see no reason for this, because the sizes indicated for (properties) of everything only totals about 10GB.

I left 8.04 and ran 9.04, to observe what I could of the 8.04 partition.

When mounted, the 8.04 partition icon (properties) indicates it is nearly full, and so does partition editor. Using partition editor I did a file system check, and there were no problems seen, but the useage was still shown as nearly full.

Either from 9.04 or from within 8.04, a nautilus list of the filesystem and select all, and (properties) only indicates contents total of approximately 10 GB which is sort of what I would expect.

Can anyone suggest what is happening, and how I might sort this anomaly out please?

---

### Post by candtalan on 2009-07-24
Solved it, I think.

Using gksu nautilus (carefully) I saw that root had a lot of files in its trash, approximately 36GB.
rm -r /root/.local/share/Trash/files
deleted these (using sudo) ok

Why had the problem happened?
I am not absolutely sure but I am using 
sbackup
version 0.10.4
 doing daily backups to another internal drive which would normally get mounted and stay mounted. For some reason I think yesterday I unmounted this drive for a time and I think sbackup does not play nice if its expected destination is missing, for example:
[http://blog.rvdavid.net/30-gb-root-partition-full-how/](http://blog.rvdavid.net/30-gb-root-partition-full-how/)
I am not sure this totally explains the cause but it seems pretty close.

---

### Post by philinux on 2009-07-24
Yep backups can cause this.

Good write up here. But you solved it yourself.
[http://ubuntuforums.org/showthread.php?t=898573](http://ubuntuforums.org/showthread.php?t=898573)

---

