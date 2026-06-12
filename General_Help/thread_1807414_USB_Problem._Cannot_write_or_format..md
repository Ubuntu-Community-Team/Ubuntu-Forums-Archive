---
title: "USB Problem. Cannot write or format."
date: 2011-07-19
forum: General Help
---

### Post by nnikolov06 on 2011-07-19
Hi all!
I have a 8GB USB drive that recently started to behave improperly. And by started I mean that my dad decided he'd use it to make a bootable drive and succeeded in breaking it.
I tried formatting and zeroing the drive with dd but no luck. It seems to finish normally, but everything remains the same. Then I read a similar thread here that worked for one guy and tried working it that way but again could not manage it. It using sfdisk and the negative result might have been because I hadn't used it before so didn't know exactly what I was doing.
Anyway, the situation is absolutely the same: cannot format/erase partition,  cannot format/erase/write data, errors are spewed out like - 
Error creating partition table: helper exited with exit code 1: Error calling fsync(2) on /dev/sdb: Input/output error 
OR 
Error creating partition table: helper exited with exit code 1: Error calling fsync(2) on /dev/sdb: Input/output error
If anyone has any ideas about this I'd be very thankful for the assistance!

---

### Post by foutes on 2011-07-19
Have you tried Gparted to delete the partition?

---

### Post by nnikolov06 on 2011-07-19
That's the thing. When the USB is connected the contents are listed. I can see files/folders etc. But in gparted it says unallocated. The only thing there is create partition table which errors in "Error while creating partition table."

---

### Post by nnikolov06 on 2011-07-19
Also here is the terminal output when trying to use gparted:
Cannot have a partition outside the disk!
Cannot have a partition outside the disk!
Input/output error during write on /dev/sdb
Error fsyncing/closing /dev/sdb: Input/output error
Cannot have a partition outside the disk!

---

