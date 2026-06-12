---
title: "Help! Missing Directory!"
date: 2011-10-25
forum: General Help
---

### Post by cbeneke on 2011-10-25
First off, I'm running 64 bit Ubuntu 10.04 on a Core i7 machine with 6gb of RAM.

I had a directory on a software RAID array that is now missing all files and folders that it contained previously.  Coincidentally there was a power failure this weekend while I was out of town.

The RAID array that I have is comprised of two 2TB drives mirrored with RAID 1 using mdadm.  The RAID array /dev/md0 was mounted at /home/chris/Raid/, and contained subfolders such as cbeneke, documents, movies, music, etc.  All the subfolders are intact and are not missing any files except the cbeneke folder which is completely empty.

On top of that, the cbeneke folder had no permissions on it when I tried to access it.  ls -l showed that the permissions were d---------.  I did a sudo chmod 700 on it, then opened it to find that there was no longer anything in it.  df -h indicates that the raid array is only 53% full when it should be in the neighborhood of 75%.

I checked lost and found and there was nothing there.  I ran sudo fsck /dev/md0, and no errors were returned.  I even checked my command line history and I can't see any commands which could have inadvertently deleted the directory.

I'm very puzzled as to where the data went and if there's anything I can do to recover it and prevent this from happening in the future.  I decided to spend the money to build a raid array in order to protect my data from this sort of thing!

Any help would be greatly appreciated.

---

