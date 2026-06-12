---
title: "Should i use quotations when concatenating path names in bash scripts"
date: 2010-01-22
forum: General Help
---

### Post by Andreas1 on 2010-01-22
```
#!/bin/bash
dir="/dir"
subdir="subdir"
filename="filename"

rm $dir/$subdir/$filename

rm "$dir/$subdir/$filename"
```

which one should i use?
NOTE: i know what the difference is, and i am not using whitespaces anywhere, but my question is: is it common use to use the quotations in such a case anyway to make the script more robust?

---

### Post by Saiko Berry on 2010-01-22
Works better for syntax highlighting ;)

---

