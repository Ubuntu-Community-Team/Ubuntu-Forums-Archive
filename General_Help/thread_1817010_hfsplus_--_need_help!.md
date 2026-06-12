---
title: "hfsplus -- need help!"
date: 2011-08-02
forum: General Help
---

### Post by akotlarsky on 2011-08-02
I am using Ubuntu in virtual machine (VirtualBox) on a Windows PC. I created a virtual disk with hfslpus file system on it (with no journaling). Then I mounted the disk to /mnt/hfsplusdisk directory. Everything seemed to be ok -- I could read and write to /mnt/hfsplusdisk/ with no problems. But after I rebooted Ubuntu (and manually mounted the disk again, just like the first time) I could only read from it -- the write operation is no longer permitted (the message says it's read-only file system). The files I created before were still there and I can still read them, but not write. How can it be possible? Any help/hint on how to make it writable would be greatly appreciated!

---

