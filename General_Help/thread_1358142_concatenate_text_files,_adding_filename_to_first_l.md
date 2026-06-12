---
title: "concatenate text files, adding filename to first line"
date: 2009-12-18
forum: General Help
---

### Post by GOwin on 2009-12-18
I have a folder containing scores of text files. I'd like to add the filename of each file as the first line of text for each file, then concatenate them all.

---

### Post by Chronon on 2009-12-18
I'm no scripting wizard, but it seems like you could whip up a for loop to "cat" all of the files and their filenames in a directory and redirect to a new file.

---

### Post by falconindy on 2009-12-18
sed is your friend.

```
ls | while read file; do
  sed -i -e "1i$file" "$file"
  cat "$file" >> /path/to/big/file
done
```

---

### Post by GOwin on 2009-12-18
Great job. Thanks

---

