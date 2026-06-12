---
title: "How Do I Access windows files in Dual Boot ?"
date: 2010-05-01
forum: General Help
---

### Post by whitetimer on 2010-05-01
Hi All

I have a dual boot, windows 7 & Xubuntu Lucid and i'd like to be able to access some files in my windows documents folder from within Xubuntu ...

How do i do this please ?

Many Thanks

:popcorn:

---

### Post by Skorzen on 2010-05-01
What's the output of the following command?
```
df -H
```

To access Windows (NTFS partition) files from any GNU/Linux distribution, you must mount it in some location (eg. /mnt/win) and set permissions to make them accessible for your user (using the 'chmod', 'chown' and 'chgrp' commands).

---

### Post by whitetimer on 2010-05-01
> **Skorzen said:**
> What's the output of the following command?
```
df -H
```To access Windows (NTFS partition) files from any GNU/Linux distribution, you must mount it in some location (eg. /mnt/win) and set permissions to make them accessible for your user (using the 'chmod', 'chown' and 'chgrp' commands).


Thanks for that, but just tried gigolo and i got the files sorted .... 

Thanks anyway

:)

---

