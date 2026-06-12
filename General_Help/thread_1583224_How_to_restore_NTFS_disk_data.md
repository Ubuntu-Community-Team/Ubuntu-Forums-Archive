---
title: "How to restore NTFS disk data?"
date: 2010-09-27
forum: General Help
---

### Post by r.osmanov on 2010-09-27
Hi. I've occasionally changed HDD filesystem type in Disk Utility from NTFS to Linux Extended :confused:. It created an extended partition containing some other partitions instead of NTFS.

No data available now. How can I restore it?

Help me please.

Regards.

---

### Post by luvshines on 2010-09-27
Did you use format option to change the partition type ?

---

### Post by r.osmanov on 2010-09-27
Thanks for the reply. 

Sorry for disturbing. Just restored with TestDisk utility :P
Ran deep scan for partitions(quick scan doesn't see NTFS) and changed partition type to NTFS (0x07).

Now disk contains 597GB Extended partition with NTFS partition of the same size and 403GB unallocated space. It seems all data is available now. Gotta switch everything to Ext4 :)

Thank you!

---

### Post by luvshines on 2010-09-28
Gud to know that the data recovery was successful. Testdisk has done it again :)

'testdisk' is surely a masterpiece.
Just recently, it saved me all my precious movies, gamez treasure collected over past 4-5 years. I was on the verge of losing everything I had in my external HDD when the jugglery of HDD between linux and windows corrupted the filesystem

But 'testdisk' proved to be 'THE SAVIOR'

---

