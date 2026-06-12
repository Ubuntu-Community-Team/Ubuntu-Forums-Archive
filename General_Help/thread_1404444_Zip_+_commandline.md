---
title: "Zip + commandline"
date: 2010-02-11
forum: General Help
---

### Post by Hawk__0 on 2010-02-11
I'm zipping some files via commandline using the following command:
```
zip -r -q file.zip files
``` 

the only problem is that I can't figure out how to remove the preceding directory path.  EG:

the zip will contain /home/user/files/

I only want it to contain the "files" directory.  This is tricky because if I use the -j switch to junk directories, it junks the directories inside the files/ folder.

Any way around this?

---

### Post by audiomick on 2010-02-11
edit:
sorry, I didn't read your post carefully enough.

I assume you have already read the man page
```
man zip
```

---

### Post by Hawk__0 on 2010-02-11
Sure have.

---

### Post by Hawk__0 on 2010-02-11
I just stated using 7zip instead.

---

