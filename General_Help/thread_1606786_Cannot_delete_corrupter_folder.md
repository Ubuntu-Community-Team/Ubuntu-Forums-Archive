---
title: "Cannot delete corrupter folder"
date: 2010-10-26
forum: General Help
---

### Post by Fender89 on 2010-10-26
I've got a corrupted folder on an external HDD. It happened because the drive was unplugged while still trying to put files to it. Is there any way i can delete the folder and all the files in it without formatting? 

There's a large amount of data on there and I've got nowhere big enough to backup to for a format.

---

### Post by efflandt on 2010-10-27
What type of file system is on the drive?  That will determine what to use to fix it.

---

### Post by Fender89 on 2010-10-27
Ntfs

---

### Post by WorMzy on 2010-10-27
You can try ntfsfix on the partition, though there's no guarantee that will actually fix anything. If you have Windows installed, run chkdsk on it instead.

---

