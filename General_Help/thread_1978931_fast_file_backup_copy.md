---
title: "fast file backup copy"
date: 2012-05-12
forum: General Help
---

### Post by v2kkim on 2012-05-12
I like to make several big folders copy/update to the USB memory stick for backup everyday.
cp -r -u  is not my favorite here, because it takes too long.

I want to copy only new files changed 1 or several days ago, only 1 or 2 times a day.
Bottom line is I only want to check the file date and copy new files, to USB flash memory,
to make it fast. 
  
The flow wil be :  
  (1) read files in specified folders
  (2) Check if file date was modified less than 1 day,
  (3) If no, skip, if yes then make copy to USB memory, maintaining directory structure.
  (4) Say, only 3 files modified within 1 day then only 3 files will be copied, and directories has to be
        created in memory stick if not-exist.

Thanks for help.

---

### Post by sudodus on 2012-05-12
I think you can use ***rsync*** to do that. It is much more advanced than cp for backing up or syncronizing. Read more in the man pages
```
man rsync
```

---

### Post by codemaniac on 2012-05-12
> **sudodus said:**
> I think you can use ***rsync*** to do that. It is much more advanced than cp for backing up or syncronizing. Read more in the man pages
```
man rsync
```

+1 for rsync .I personally prefer rsync over scp .

---

