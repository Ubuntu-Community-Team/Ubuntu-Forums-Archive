---
title: "Can't write data to ntfs drives"
date: 2011-11-13
forum: General Help
---

### Post by maheshdevabhaktuni on 2011-11-13
I'm using windows7-64bit and ubuntu11.10-64bit
when i tried to copy and paste data in ubuntu ,i cant select the paste option and ctrl+v option also not working
even i can't create a document or new folder or rename any folder
when i tried to change the permissions  it's displaying like that in the image
even after formatting the drive,no change
please help me anybody:(:(:(:(:(:(

---

### Post by BillyBoa on 2011-11-13
It's a little complicated to change permissions to a NTFS drive through Linux. 

Go to your Win 7 part and from there change permissions to the drive.

---

### Post by Cyclane on 2011-11-13
How did you mount it?
Please paste the output of 'mount'

---

### Post by Mark Phelps on 2011-11-13
First of all, if you're trying to write to your Win7 OS partition from inside Ubuntu -- STOP!  That risks corrupting the Win7 filesystem and rendering it unbootable.

If, instead, it is a DATA partition, meaning, there is no OS on it, then if it was not cleanly dismounted in Ubuntu the last time you used it, it could very well have been mounted read-only -- the default in Linux when it encounters filesystem problems with NTFS partitions.

Also, the permission handling in Linux filesystems and NTFS filesystems is very different.  So, trying to change permissions on the NTFS folders or files is most probably NOT going to work.

---

