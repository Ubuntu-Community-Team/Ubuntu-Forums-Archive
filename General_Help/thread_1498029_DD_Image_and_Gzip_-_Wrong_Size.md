---
title: "DD Image and Gzip - Wrong Size?"
date: 2010-05-31
forum: General Help
---

### Post by ks07 on 2010-05-31
Hey all,
Have a HDD with a large XP ntfs partition and a small fat32 recovery partition which I'm trying to image and compress to backup onto a USB drive. It appears to have worked perfectly, although after opening the archive using File Roller to check the contents, the image file shows a size of 1.1 GB - obviously way too small for a windows install and recovery. However, the size of the .gz file on the disk is 14.8 GB, which sounds about right. Why is the uncompressed size so much smaller than the archive? Should I try again?

*More Info:*
```
gunzip -l 310510windrive.gz 
         compressed        uncompressed  ratio uncompressed_name
        15883400630          1128095744 -1308.0% 310510windrive
```
(Testing the archive with -t returned nothing)

Command used:
```
sudo dd if=/dev/sdb | gzip > ./310510windrive.gz
```

Before starting the backup, I defragged (yawn) and used dd to zero the blank space on the ntfs partition, hoping to decrease archive size.

---

### Post by ks07 on 2010-05-31
Update: Have been searching for similar errors and have found [this in the gzip FAQ]("http://www.gzip.org/#faq10"), related to a file size bug with files over 4GB in size. However, it seems rather outdated and is supposedly fixed in the version included in Ubuntu. I'm uncompressing the image right now to see if it is the correct file size - and, if so, I'll mark this as solved and report it as a bug later. If all goes to plan, it's not a serious problem and I can live with it.

---

