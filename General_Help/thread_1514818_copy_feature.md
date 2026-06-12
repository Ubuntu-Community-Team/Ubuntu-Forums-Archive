---
title: "copy feature?"
date: 2010-06-21
forum: General Help
---

### Post by victorfuts on 2010-06-21
basically this what i want to do:

sync two folders, sometime i change content in one folder, without changing the filename and path structure. when i copy the folder with newer file to old folder, i want to only replace the newer files but do nothing to other files.

is there a way for ubuntu check the version of the file and do the copying action?

---

### Post by victorfuts on 2010-06-21
btw, i assume that comparing two files is faster than copying and replace.

i only want to do this because i want to copy a large quantity of mp3 files.

---

### Post by ThesaurusRex on 2010-06-21
```
cp -u SOURCE DEST
``` should do it. If you do ```
cp --help
```, -u reads "copy only when the SOURCE file is newer than the destination file or when the destination file is missing." Hope that helps.

---

