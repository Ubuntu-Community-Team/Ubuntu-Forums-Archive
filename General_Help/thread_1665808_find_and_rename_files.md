---
title: "find and rename files"
date: 2011-01-12
forum: General Help
---

### Post by Diwin on 2011-01-12
I need to find and rename all .JPG files to .jpg in a folder with subfolders. How would I go about this?

---

### Post by sisco311 on 2011-01-12
There are many ways. If you are using bash, try something like:
```

shopt -s globstar
cd **path/to/dir**
for file in **/*.JPG; do **echo** mv -b -- "$file" "${file%.JPG}.jpg"; done

```

The above code will only print the mv commands used for renaming the files. To actually rename them remove the **echo** command. And of course, you have to replace **path/to/dir** with the real path to the directory.

---

