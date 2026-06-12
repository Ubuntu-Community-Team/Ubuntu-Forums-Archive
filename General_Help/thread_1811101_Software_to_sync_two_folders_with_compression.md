---
title: "Software to sync two folders with compression"
date: 2011-07-24
forum: General Help
---

### Post by jonta on 2011-07-24
Hello

I currently have a Ubuntu 10.04.2 server with a large data directory on a raid5.
What i want to do seems quite simple to me, i want to backup this directory to an USB disk i have mounted.
I have used rsync in the past, however i still want the data that has been transferred to the USB disk to be compressed since the USB backupdisk is smaller then my data directory.
And if possible i also want it to consolidate the data, so if there are two files that are exactly the same, it only stores one of them and symlink the other.
I also still want the rsync functionality so if part of a file has changed it only needs to upload the changes.

Are any of you aware of such software?
I remember reading somewhere a long time ago about software that did the consolidation of files at least, so i know it's possible.

---

