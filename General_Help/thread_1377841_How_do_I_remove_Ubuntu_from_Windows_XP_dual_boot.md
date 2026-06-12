---
title: "How do I remove Ubuntu from Windows XP dual boot?"
date: 2010-01-10
forum: General Help
---

### Post by Vignesh S on 2010-01-10
My sister isn't using Ubuntu on her netbook (that was me that used it), but it fell out of use on it. So I figured that its time to remove it. So my question is: how would I go about removing Ubuntu 9.10 from an Ubuntu/Windows XP dual boot?

---

### Post by cariboo on 2010-01-10
You would remove Ubuntu the same way you would any other OS, just format the partition to whatever filesystem you want, then fix the mbr. Boot from your Windows install disk, and go into the recovery console and run fixboot and fixmbr.

---

### Post by gabo.cr on 2010-01-10
You can also do that with the Ubuntu Live CD.

---

### Post by Vignesh S on 2010-01-10
Alright, I deleted the partition. Looks like that the mbr isn't going to be a problem because after I deleted the partition, XP is already booting up without any problems.

But how would I transfer the extra space I now have onto the ntfs XP partition?

---

### Post by steveneddy on 2010-01-10
Use the partition tool in XP to merge the partitions.

---

### Post by Vignesh S on 2010-01-10
Right, I made the empty space into another NTFS partition. But the XP partition tool doesn't even let me extend the space of the C drive. 

How do I get do the partition tool in XP? Is it via running compmgmt.msc, and going into Disk management?

---

### Post by Vignesh S on 2010-01-11
Don't worry, I figured it out by using EASEUS Partition Master with the free version.

---

