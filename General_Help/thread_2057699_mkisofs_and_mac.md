---
title: "mkisofs and mac"
date: 2012-09-14
forum: General Help
---

### Post by sselt on 2012-09-14
What extensions are needed to create a disk with files readable on linux, windows, and mac os x? I read thru the manual and not sure. Is this correct or is the -hfs needed?
```
mkisofs -o cd.iso -R -J -hfs cd_dir
```

---

### Post by mcduck on 2012-09-14
Pure ISO9660 works perfectly fine on all operating systems, you only need the -hfs option if you want to save additional information HFS file system would have (creator, file type and some other extra information about the files that Finder can understand).

---

### Post by sselt on 2012-09-14
> **mcduck said:**
> Pure ISO9660 works perfectly fine on all operating systems, you only need the -hfs option if you want to save additional information HFS file system would have (creator, file type and some other extra information about the files that Finder can understand).

Thanks mcduck, that cleared up some confusion!

---

