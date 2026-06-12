---
title: "Grsync and symlinks"
date: 2012-05-15
forum: General Help
---

### Post by habana on 2012-05-15
I have a problem backing up my Home folder. This is a separate partition on a SSD and contains all the hidden files and a single symlink to a HDD mounted at /mnt/data. The symlink is ```
ln -s /mnt/data/bill /home/bill/data
```. 

I wish to backup Home to a second HDD at /mnt/data1 using Grsync. Using the standard options I performed a dry run (-r-n-t-x-v) and the output shows all the hidden files/folders and ignores the symlink as expected. I have looked at the rsync man page and this indicates I should add the -L option which I duly added to the 'Additional Options' window of Grsync. Running this only adds the folder data/ to the output, not all the folders and files within. It's as if the recursion doesn't work over a symlink.

What am I doing wrong?

---

### Post by papibe on 2012-05-15
Hi habana.

There is some conflict with -x and -L.

-x won't allow to follow the symlinks if they are on another filesystem.

If I were you, I'd remove -x, and use excluding rules (--exclude) to avoid crossing file systems (e.g. ~/.gvfs).

Hope that helps,
Regards.

---

### Post by habana on 2012-05-16
Hi papibe

Thanks for your response. I've looked at the rsync man page and I can see how --exclude works. What I don't understand is what is meant by crossing file systems. Surely, everything under / (e.g. /home, /mnt/data) is part of the same file system? However, you must be right as I tried a dry run with -x removed and a number of circular references related to .wine appeared. Once I excluded .wine, I got the result I required :)

Thanks very much for this, I shall mark it as solved

Regards
Bill

---

### Post by papibe on 2012-05-16
Well, the term 'filesystem' can be ambiguous.

For rsync means, partition, or mount point.

I assume your /home partition is in different partition than /. In this case, the option -x won't allow rsync to go into /home/bill/data because it points to another partition.

Does that clarify things a little bit?

Kind Regards.

---

### Post by habana on 2012-05-16
Hi papibe

Yes, that clears it up completely.

Many thanks and regards
Bill

---

