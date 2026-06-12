---
title: "Accidentally replaced folder with symlink to folder"
date: 2011-08-22
forum: General Help
---

### Post by The Wanlorn on 2011-08-22
The way I have my drives set up, a bunch of the main user folders (ie Documents, Music, etc) are symlinks to the actual folders on another partition.  I was transferring data from my old drive to my new drive and went to manually copy over the links.  Except, instead of copying them from the old drive to the new drive and replacing the actual (empty) folders there, I copied them to the second partition on the old drive, where the links replaced the folders they were linking to.

Is there any way to get at the data that was in those folders now?  It's not an epic tragedy, since everything is backed up, but I'm currently on vacation and won't be able to restore anything for another two weeks.  It'd be nice to be able to recover, say, my music from the old drive now.

Any help in saving me from my own idiocy would be very much appreciated

---

### Post by lmarmisa on 2011-08-22
Try to mount the second partition of your old drive where the files are stored and you will be able to copy (or move) them where you wish. Select Places -> YourPartition. I do not know if this feature of Gnome is available in Ubuntu 6.06. Anyway, a manual mount is always possible.

---

