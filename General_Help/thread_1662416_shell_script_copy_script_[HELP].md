---
title: "shell script copy script [HELP]"
date: 2011-01-08
forum: General Help
---

### Post by elroulade on 2011-01-08
Hello

I need a simple shell script, that copies all the files in a folder exept 1 file to another location, but i dont know how to do it myself.

---

### Post by McNils on 2011-01-08
```
#!/bin/sh
DEST=/dir1
SOURCE=/dir2
DO_NOT_COPY=file.txt
find "$SOURCE" -maxdepth 1 -type f -a ! -name "$DO_NOT_COPY" -exec cp {} "$DEST" \;

```

---

### Post by papibe on 2011-01-13
Here's another way to do it:
```
$ rsync -av --exclude='file.txt'  source_dir/ dest_dir/
```
Regards.

---

### Post by sisco311 on 2011-01-13
This one should work in bash:
```
shopt -s extglob
cd path/to/source
cp !(filename) path/to/dest
```

---

