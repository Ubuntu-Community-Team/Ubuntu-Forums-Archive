---
title: "Cat Large Files"
date: 2010-07-04
forum: General Help
---

### Post by Tylerjd on 2010-07-04
I have a bunch of 2.2 GB files that I need to cat into one large file, but I run into the file size limit. I run the command```
cat sda.ntfs-img.a* > sda3.ntfs-img
```And it comes back with the error explained above. I am running this on Ubuntu 10.04 amd64.

---

### Post by CharlesA on 2010-07-04
what file system are you using, and what is the exact error message?

---

### Post by Tylerjd on 2010-07-05
> **CharlesA said:**
> what file system are you using, and what is the exact error message?
  Thanks for the question, CharlesA, it actually helped me self solve the issue. What I was doing was running this on a FAT32 External HDD, but since it was fat 32, it had a 4 GB limit and the file was a total of 7.9 GB. I cp'd the files over to a EXT4 drive and cat'd them there, and it went without a hitch. Thank You.

---

### Post by CharlesA on 2010-07-05
Yup, FAT32 has a limit of 4GB per file. :-)

Glad you got it working.

---

