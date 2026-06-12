---
title: "migrate to a larger HD, dumping windows...."
date: 2011-08-13
forum: General Help
---

### Post by goodbye-windows(tm) on 2011-08-13
I currently use Xubuntu on a dual boot system, a laptop. The hard drive is to small (30 GB shared between Xubuntu and windows), so I want to clone the existing drive, but I do not want to clone windows.

I bought a 120 GB hard drive, and want to dump windows totally. 

If I download clonezilla and burn it to a cd, can I instruct it to only clone the Xubuntu system?

I think I would run clonezilla from a cd, download everything to my USB drive, then remove the small hard drive. Then, install the bigger drive and restore everything to the newer and larger drive.

Will this work???

Please note, I want to archive the original (smallish) hard drive, just in case...

TIA

Art

---

### Post by JonasPed on 2011-08-13
I believe it should be possible to only clone a single partition. At least clonezilla.org says it can clone single partitions or whole disks.

---

### Post by Elfy on 2011-08-13
Never used clonezilla but you have other options - delete windows, resize the existing / or delete windows and create a new partition in the unallocated. Create partition(s) in the new drive. 

Mount the new partitions in fstab at boot. Use them for data storage.

---

