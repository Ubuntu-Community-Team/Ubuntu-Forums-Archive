---
title: "Ampache Catalog From External HD Problem"
date: 2010-06-04
forum: General Help
---

### Post by ephman on 2010-06-04
hi,

i've searched and can't seem to find a way to fix my problem. i can not seem to create a catalog. i get this error:

Error: /media/lacie_mount/Music is not readable or does not exist



my media is stored on an external NTFS drive that is attached with an eSATA cable. i created a mount point in fstab with these options:

/dev/sdc1 /media/lacie_mount ntfs default 0 0
/dev/sdc1 /media/lacie_mount ntfs umask=000


however no matter what i do, or try the drive does not seem to be recognized by Ampache. if i put files on my local drive, no problem i can create a catalog. obviously i'm missing something.

i suspect there must be something in either apache or the php.ini file that i'm missing? any help would be really appreciated and good karma will come back to you.

thanks,
ephman

---

### Post by ephman on 2010-06-05
got it!  had to edit the fstab file to show

```
/dev/sdc1 /media/lacie_mount ntfs defaults,noexec,umask=002       0       0
```

and now i've cataloged my library, and can play.

---

