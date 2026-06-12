---
title: "Mounting without Formatting"
date: 2010-02-12
forum: General Help
---

### Post by Deadseraph on 2010-02-12
I've been working on restoring my computer after a crash, and evidently my xfs root file system was unmounted or something, so when I go back in to re-install, it shows up without a mount point.  When I go to mount, I have the option to mount it back to / without formatting it.  My question is, will this save my files already in the partition, and if not, is there some way to access these files before I DO lose them?

Thanks in advance for any help!

---

### Post by bruno9779 on 2010-02-12
That will overwrite the data.

Your best option is possibly loading the live CD and use it to browse and copy the partition.

Another approach could be using testdisk (partition recovery tool) but it is a very advanced tool that can be quite difficult to use

---

### Post by Deadseraph on 2010-02-12
I booted from a Live CD, but when I try to mount the 11GB filesystem (xfs partition) I get 2 errors, one stating that an operation is already pending and another saying there was an error because it couldn't read the "superblock", anything to fix/get around this?

---

### Post by bruno9779 on 2010-02-12
I would try to recover the partition running [testdisk]("http://www.cgsecurity.org/wiki/TestDisk") from the live session.

It is a very powerful tool, but not very straight-forward for first time use.

---

