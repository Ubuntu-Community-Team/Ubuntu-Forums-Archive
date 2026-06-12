---
title: "find command for multiple filenames stored in list"
date: 2011-05-03
forum: General Help
---

### Post by fdiz on 2011-05-03
I searched the forum and didn't find any threads that seemed to answer this question...

I have a large directory of files, and dozens of subdirectories on a remote box I have ssh access to.  I need a subset of these files copied to another folder.

Example:

directories
parent
-sub1
-sub2
-sub3

files I want (the files are all the same format, but some have extensions and others dont)
1100
1215
1322
1442
1500
1512

Unfortunately, I need a lot of files, and plan to do this on a regular basis (the files I need will be different each time)

I was thinking it would be nice to be able to put the filenames in a text file (one filename per line) and use the find command to copy the files (I don't necessarily know which subdirectory the file will be in).

This is the command I used to do this one file at a time

```
find . -iname 1322\* -exec cp {} PATH_TO_SAVE_FOLDER \;
```Is there a way to do this with a text file? I've read the documentation for the find command and can't find a way to use a list of filenames stored in a text file as input (but that is an option for the file() command.

Thanks!

---

### Post by TeoBigusGeekus on 2011-05-03
Create a list of the files you want copied, name it list and save it in the parent directory.
Navigate in there and give
```
cat list|while read line;do find ./ -iname "$line" -exec cp {} /path/to/where/you/want/your/files/copied \;;  done
```

---

### Post by fdiz on 2011-05-03
Thanks!

I didn't think to use cat

---

