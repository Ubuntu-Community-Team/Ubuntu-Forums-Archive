---
title: "Nautilus file properties"
date: 2009-07-24
forum: General Help
---

### Post by sidewalkcynic on 2009-07-24
When files are moved to another storage device they loose their properties (emblems, notes, etc) - is there any way to retain the properties?

---

### Post by ajgreeny on 2009-07-24
Is the other device a fat32 or ntfs drive?  If so I don't think you can do it as they do not support the linux file properties.  You can either format the drive to a linux file system eg, ext3 or I think you can tar the files and then copy the archive.  The files in that will retain their permissions, I think, when copied back and untarred.

---

### Post by sidewalkcynic on 2009-07-24
I never thought of doing it that way - it probably saves space, as well?
... and, time. But, yes, the device is the same as the hardrive ext3.

But, another thing I am concerned about, is that I, basically, want to be able to defragment the files by sorting them into the external device and then back to the hardrive - is that accomplished in the tar compression cycle?

Thanks, Ron

---

### Post by jenkinbr on 2009-07-24
> **sidewalkcynic said:**
> I never thought of doing it that way - it probably saves space, as well?
... and, time. But, yes, the device is the same as the hardrive ext3.

Thanks, Ron
Only a slight bit - for real space saving, you could compress the *.tar file into a *.tar.gzip

---

