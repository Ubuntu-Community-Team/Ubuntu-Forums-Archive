---
title: "Back up time machine back ups from a mac to ubuntu"
date: 2010-05-17
forum: General Help
---

### Post by lb121 on 2010-05-17
Hi

I was wondering whether it was possible to back up time machine back ups from a mac in ubuntu. 

I use a mac at work and use time machine to back up to an external hard drive which i take home each day. I wish to back up the time machine back ups off the external hard drive each day to my computer at home just to be safe is this possible?

I have managed to open the hard drive and have enabled view hidden files so i can see all the files but i am unable to copy them due to permission errors

---

### Post by sedawk on 2010-05-17
I have no experience with MacOS disks on Linux, but
if you cannot copy the files, does that mean
you also cannot view the content of the files?

You can run ls -l on a directory so we can see
the permissions files have.

But back to Time Machine:
To make Time Machine work and efficient, Apple changed
their file system (handling) to support hardlinked directories.
Instead of hardlinking every file in a directory they are
now able to create hardlinks if directories are identical.
( Normally you do not want to have this because there is a danger
of an endless loop when the system traverses through the
directory hierarchy. But Apple solved that problem ).

This is something a Linux filesystem cannot do.
Even if you use rsync with "-H" option to preserve
hardlinked files (expensive operation) it most likely
will not do that for directories and disk usage
will go sky high when cloning the time machine drive.

(Actually you can use rsync to create a backup similar
 to Time Machine but without directory hardlinks you
 need much more file hardlinks and you have to cleanup
 the backups regulary )

---

