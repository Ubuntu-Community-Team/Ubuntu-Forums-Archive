---
title: "ntfs vista missing folders"
date: 2011-08-07
forum: General Help
---

### Post by TTGRULES on 2011-08-07
Old vista laptop crashed so I ripped out the hard drive and stuck it into my ubuntu 10.04 machine. It mounted easily, but half of the folders don't display in nautilus. I've tried nautilus in root. listing them from the command line works fine. the permissions on the folders are set to exactly the same as the folders that display fine. Any Ideas?

---

### Post by dcstar on 2011-08-08
> **TTGRULES said:**
> Old vista laptop crashed so I ripped out the hard drive and stuck it into my ubuntu 10.04 machine. It mounted easily, but half of the folders don't display in nautilus. I've tried nautilus in root. listing them from the command line works fine. the permissions on the folders are set to exactly the same as the folders that display fine. Any Ideas?

Install the **ntfsprogs** package and run **ntfsfix** on the partition.

---

### Post by Mark Phelps on 2011-08-08
Good luck with ntfsfix.  Sometimes it DOES work; but other times, especially when the filesystem corruption is severe, it does not.

If it doesn't work, since there is no actual Linux equivalent of CHKDSK, your only other option would be to hook the drive to an MS Windows PC and try running CHKDSK on it.

---

