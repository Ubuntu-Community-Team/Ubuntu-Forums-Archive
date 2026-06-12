---
title: "How to copy a file mode from one file to another?"
date: 2010-07-30
forum: General Help
---

### Post by ygoe on 2010-07-30
I'm writing a bash script that does some automated text replacement in a specified file. It updates a series of placeholders to their actual value, using sed. The result is directed to a temporary file which is then moved back to the input file name.

The new file has a default mode of 0644, no matter what the input file's mode was. Modes like 0755 or 0600 will be lost then.

How can I transfer the file mode from the input file to the temporary file before moving it back? chmod can set a file's mode, but how cat it be retrieved in the same format?

---

### Post by sisco311 on 2010-07-30
Why don't you edit the file in place?
```
sed -i.backup [OPTIONS] {scrip} file
```

---

### Post by ygoe on 2010-07-30
> **sisco311 said:**
> Why don't you edit the file in place?
Good idea, thank you. I wasn't aware of that option but it works very well. It makes my script a bit shorter. :-)

---

### Post by prodigy_ on 2010-07-30
In reply to the original question, it's possible to get octal permissions with **stat -c "%a"** command and apply them to another inode with **chmod**. Example:
```
SAVED_PERM=$(stat -c "%a" /path/file)
chmod $SAVED_PERM /newpath/newfile
```

---

