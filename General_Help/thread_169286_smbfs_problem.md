---
title: "smbfs problem"
date: 2006-05-02
forum: General Help
---

### Post by sharperguy on 2006-05-02
Hi

Today i sucessfully managed to mount an smbfs directory using fstab.

However, the other directory i want has a space in the name and simply using quotes makes no difference. Is there some sort of code i can use to replace the space?

---

### Post by yota on 2006-05-02
Try to escape spaces with backslash (replace '\ ' to ' ').

It should work... but I've never tried in fstab!

---

### Post by sharperguy on 2006-05-02
This dosnt work im afraid, it jsut detects it as a backslash

and putting a backslash THEN a space dosnt work either

---

### Post by yota on 2006-05-02
Mhh... you're right: this one was a bit tricky and some study was needed.
Sorry to have given a wrong hint before.

In 'man fstab' I've found the answer:

> 
If the name of the mount point contains spaces these can be escaped as `\040'.


and so I was able to mount a share named "folder with spaces" with this line in fstab:
```

//servername/folder\040with\040spaces  /mnt/tmp cifs username=***,password=*** 0 0

```

---

### Post by sharperguy on 2006-05-19
cheers, i jsut got the admin to change it the spaces to underlashes, but he can change it back now. :)

---

### Post by redistributer on 2006-05-19
you can also use %040% to recongnize a space

---

### Post by sharperguy on 2006-05-21
thanks

---

