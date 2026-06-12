---
title: "Data disappeared from NTFS filesystem"
date: 2010-11-11
forum: General Help
---

### Post by Admiral Yi on 2010-11-11
I recently tried to access some files using linux on a hardrive formatted with NTFS that I use as a share between linux and windows. All the files in one folder have disappeared. I'm 100% sure I didn't delete the files. 

Is this just one of the problems that can occur when using NTFS with linux? Is there an easy way to get the files back? I don't know how long they've been missing, but I haven't written much data to the disk in a while so they could still be there.

---

### Post by CharlesA on 2010-11-11
Best way to check is to boot into Windows and run chkdisk on that drive.

If they were deleted they'd probably be in a folder named .Trash or something like that.

---

### Post by Admiral Yi on 2010-11-11
There is no .trash file unfortunately. I was wondering if there were any linux tools for doing the same, as I no longer have windows (that's why I was trying to access the data, so I could move it off the drive)

---

### Post by CharlesA on 2010-11-11
There are no linux tools to deal with NTFS the same way that Windows does.

---

### Post by Admiral Yi on 2010-11-11
Ah ok. I may still have a windows disk lying around, I'll try that.

---

