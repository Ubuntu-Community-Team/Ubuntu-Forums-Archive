---
title: "Data loss, partition overwritten EXT4"
date: 2012-08-03
forum: General Help
---

### Post by edmundjc on 2012-08-03
Hi all,

As the thread title suggests, I've managed to write a new partition table to a drive that contained a multitude of valuable datas.  It happened as I was re-installing ubuntu 12.04 to a RAID set present on the machine.  The drive itself was not to be touched, only mounted to a specific directory once the install had completed.  I had specified that the partition should not be formatted and whatnot, but at this point, I can't say whether or not I had properly set it up in the install's partition manager.

Once ubuntu had finished installing, I checked the mount point, only to find a squeaky-clean directory in place of all my data.  No data whatsoever has been written to the drive since, and I was able to recover some of the files, though I suspect the tool I used (Raise Data Recovery for Ext2/3/4) was not terribly thorough.  I believe the data is all still probably there, and I was wondering if anyone had any ideas?

I've been able to find a number of forums and discussions on the subject, but none yet that address the (presumed) re-write of the partition table.

Thanks!
-Jer

---

### Post by The Cog on 2012-08-03
photorec will recover lots of files. Use it from a CD and write the files to an external drive - don't write to the damaged drive. But it only gives them numbers, do you will have thousands of files to try and identify afterwards. It's a last resort.

---

### Post by edmundjc on 2012-08-03
Thanks much.  I'll keep that in mind.  I'm hoping it doesn't come to that, as it is a 2TB drive that is about 90% full (There's a lesson about eggs and baskets in here somewhere).  I can live without recovering the directory structure, but filenames would be real important.

---

