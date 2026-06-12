---
title: "Clonezilla Help"
date: 2010-07-02
forum: General Help
---

### Post by brotherbbad on 2010-07-02
I have made a drive image with Clonezilla only to find out that it was split in to 2GB images... how can I "Join" or assemble these into a single image?  This has been making me crazy for days..... 

Thanks in advance.

PS Clonezilla used dd to create these images....

---

### Post by CharlesA on 2010-07-02
I don't think you can join them, since they are compressed, but look in the advanced options and tell it not to split the files.

---

### Post by duanedesign on 2010-07-02
would this work for you?


```
cat /home/duanedesign/imagefile.dd.* | dd of=/home/duanedesign/imagefile-combined.dd
```

---

### Post by CharlesA on 2010-07-02
Looking at the files that it's saved for me:

sda1.ntfs-ptcl-img.gz.aa
sda1.ntfs-ptcl-img.gz.ab
sda1.ntfs-ptcl-img.gz.ac
sda1.ntfs-ptcl-img.gz.ad
sda1.ntfs-ptcl-img.gz.ae
sda1.ntfs-ptcl-img.gz.af

I don't know if it's possible, but maybe that's cuz I've just used partclone to make the images, not dd.

---

