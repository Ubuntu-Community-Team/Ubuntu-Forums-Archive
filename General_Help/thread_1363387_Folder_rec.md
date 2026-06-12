---
title: "Folder rec"
date: 2009-12-24
forum: General Help
---

### Post by Nyg33 on 2009-12-24
hey, 
a folder has been deleted mistakely (10 g )
i cant use rec tools cause there were files with diffrence ext
how can i recover that ?

---

### Post by HomoGleek on 2009-12-24
It should be in your wastebasket?

---

### Post by Nyg33 on 2009-12-24
nope
?

---

### Post by cdenley on 2009-12-24
Was it deleted, or moved to trash? If you were using nautilus, then you would have been prompted to confirm a permanent deletion. If it was deleted, what type of filesystem was it deleted from?

---

### Post by Nyg33 on 2009-12-25
Deleted, ntfs
ubuntu 9.04

---

### Post by Mahngiel on 2009-12-25
if i understand correctly, it was a different partition's folder which was deleted?

if so, press <ctrl> + h to show hidden files. there's usually a .Trash folder there.  check it out.

---

### Post by Nyg33 on 2009-12-25
yep , 

i did it at the same time !

---

### Post by cdenley on 2009-12-28
> **Nyg33 said:**
> yep , 

i did it at the same time !

Did what at the time time?
```

sudo apt-get install ntfsprogs
man ntfsundelete

```

---

