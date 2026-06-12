---
title: "Using sed or awk to find and delete lines in a file"
date: 2010-12-21
forum: General Help
---

### Post by mcclane400 on 2010-12-21
I have a bunch of text files, all of them have a .txt extension.  They are all located in subfolders of the /MyTextFiles folder (but could be anywhere, no idea what depth).  If any line in any of the text files has the word "hello" I want to delete that entire line.  I know sed and awk are made for this problem but I can't seem to get the syntax correct.  Any suggestions?

---

### Post by sisco311 on 2010-12-21
Try:
```
sed -i '/hello/d' path/to/file
```

To match any .txt file in a directory and its subdirectories, in bash (>=4.0), try something like:
```
shopt -s globstar
cd path/to/dir
sed -i '/hello/d' **/*.txt
```


Here is another variant with find:
```
find path/to/dir -name \*.txt -type f -exec sed -i '/hello/d' '{}' +
```

---

