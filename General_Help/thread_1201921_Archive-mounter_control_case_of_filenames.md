---
title: "Archive-mounter control case of filenames"
date: 2009-07-01
forum: General Help
---

### Post by schilcha on 2009-07-01
Hi there!

I appreciate archive-mounter (right-click in nautilus on an iso-file and choose it under open-with) as a very convenient tool. However, I ran into the following problem: 

All filenames are upper-case. But, the ISO image I tried to work with contains a set of html-files with links in lower-case to other files on the CD. Consequently, none of the links are working.

If I use 'mount -o loop' to mount the same image, all filenames are lower-case and the links in the html files point to their target correctly.

My question is: is there a way to control the case of filenames of ISO 9660 filesystems mounted by archive-mounter?

I don't know how to determine relevant details of the image, but here's what I found out:
```

$ file eudralex_v20.iso 
eudralex_v20.iso: ISO 9660 CD-ROM filesystem data 'EUDRALEX_V20

```

---

