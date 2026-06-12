---
title: "convert pdf to text in a for loop"
date: 2012-01-01
forum: General Help
---

### Post by coffeecake on 2012-01-01
Hi i have a folder containing pdf's but there is a small problem because the input file names have spaces in it. And pdftotext command seem to have problems because of that.

This is how i do the conversion

```
for f in *.pdf
do
    pdftotext $f $f.txt
done
 
```Could someone please help me out

---

### Post by sisco311 on 2012-01-01
Double quote every expansion and anything that could possibly contain a special character, e.g. "$var", "$@", "${array[@]}", "$(command)". See: [http://mywiki.wooledge.org/Quotes](http://mywiki.wooledge.org/Quotes) and BashFAQ 020 (link in my signature).

```
#!/bin/bash

shopt -s nullglob nocaseglob

for file in ./*.pdf
do
    pdftotext "$file" "${file%.*}.txt"
done


```

---

