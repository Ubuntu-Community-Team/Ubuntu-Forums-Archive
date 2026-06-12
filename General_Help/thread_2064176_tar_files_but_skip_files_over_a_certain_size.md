---
title: "tar files but skip files over a certain size?"
date: 2012-09-28
forum: General Help
---

### Post by sohlinux on 2012-09-28
How can I tar files but skip files over a certain size? 

I don't want to include files over 5mb

thanks

---

### Post by hwttdz on 2012-09-28
```
tar -cf[z] my_archive.tar[.gz] `find dir_to_tar -type f -size -5M`
```

I would suggest including the z and .gz which will gzip the archive, but since you just asked about tarring...
I'd also run the find command first and make sure it's going to drop the files you think it will into the archive. 
I didn't see a way to do it directly from tar.

---

### Post by sohlinux on 2012-09-28
> **hwttdz said:**
> ```
tar -cf[z] my_archive.tar[.gz] `find dir_to_tar -type f -size -5M`
```

I would suggest including the z and .gz which will gzip the archive, but since you just asked about tarring...
I'd also run the find command first and make sure it's going to drop the files you think it will into the archive. 
I didn't see a way to do it directly from tar.

thanks but it said
tar: You may not specify more than one `-Acdtrux' option

from / folder

tar -cfz home-backup.tar `find /home -type f -size -5M`

---

### Post by hwttdz on 2012-10-23
Try:
```
tar -cz -f home-backup.tar.gz `find /home -type f -size -5M`
```

I think it's tar being picky about order and separation of options.

---

