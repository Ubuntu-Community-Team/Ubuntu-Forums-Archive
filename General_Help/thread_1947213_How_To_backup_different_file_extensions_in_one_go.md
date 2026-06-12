---
title: "How To backup different file extensions in one go"
date: 2012-03-26
forum: General Help
---

### Post by fayazali on 2012-03-26
Hi,
I have one folder which contains lot of files with different extensions i,e .doc , .xls etc. there are some folders over there also . 
I would like to backup only files but not the directories into that folder so how i can do that?

Or can i restrict some files that should not backup? means i want to exclude some files as well. 
Your help will be appreciated

---

### Post by TeoBigusGeekus on 2012-03-26
You can use find:
```
find /path/to/folder/ -maxdepth 1 -type f -exec cp "{}" "/path/to/backup/folder/{}" \;
```

If you want to exclude some files, you could add a negative name (or iname, for case insensitive search) switch. If, for example, you want to backup all the files but not the ones that end with .txt (or .TXT), you could use:
```
find /path/to/folder/ -maxdepth 1 -type f ! -iname "*.txt" -exec cp "{}" "/path/to/backup/folder/{}" \;
```

---

### Post by Vaphell on 2012-03-26
mv doesn't sound like backup (aka duplication) to me ;-)

i guess Sisco would say that you should change the order in this condition:
```
-type f ! -iname "*.txt"
```
usually there is much more files than directories so -iname part weeds out right off the bat more things than -type f (each test = 1 *stat* call i think). 


besides OP should look into some proper syncing method like rsync.

---

### Post by TeoBigusGeekus on 2012-03-26
> **Vaphell said:**
> mv doesn't sound like backup (aka duplication) to me ;-)

Oh s**t, yeah, I'll correct the post...
Good call!

---

