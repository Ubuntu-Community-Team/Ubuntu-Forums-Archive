---
title: "Slow folder and file creation"
date: 2010-08-08
forum: General Help
---

### Post by mechres on 2010-08-08
Hi,

I have a raid 5 array on an old Ubuntu 8.10 machine which has started behaving a bit odd. Whenever I try to create a new file or folder on the partition, it hangs on the file operations dialog while preparing, for something like half a minute. During this time, any attempt to access the partition also hangs.

When it finally snaps back into life, everything proceeds normally, and you can continue to create new files and folders without this delay, though eventually it will reoccur.

Any ideas what could be causing this? mdadm isn't reporting any problems with the array, and a disk seperate to the array doesn't have any problems.

---

### Post by john newbuntu on 2010-08-08
Anything interesting in the logs esp. dmesg?  How is it doing spacewise?  If nothing obvious, you could try fsck or more importantly smartctl from the CLI.

---

