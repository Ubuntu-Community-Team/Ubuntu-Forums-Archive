---
title: "Batch compress PDF files"
date: 2011-01-29
forum: General Help
---

### Post by edwbaker on 2011-01-29
I would like a program or script that will compress a whole folder of PDF files easily - any ideas?

Possibly a s script that makes use of these tools? [http://pandemoniumillusion.wordpress.com/2008/05/07/compress-a-pdf-with-pdftk/](http://pandemoniumillusion.wordpress.com/2008/05/07/compress-a-pdf-with-pdftk/)

---

### Post by tredegar on 2011-01-29
It is generally considered polite to post what you have tried, and what isn't working for you, before asking for a script.

But here goes (untested)
```
#!/bin/bash
for file in *.pdf 
do
echo Processing $file
pdf2ps "$file" "$file".ps
ps2pdf "$file".ps "$file".processed
rm "$file".ps
done
```

---

### Post by Vaphell on 2011-01-29
```
#!/bin/bash

for file in *.pdf
do
  pdf2ps "$file" "tmp_${file%.*}.ps"         # create temporary tmp_NAME.ps
  ps2pdf "tmp_${file%.*}.ps" "new_${file}"   # create result - new_NAME.pdf
  rm "tmp_${file%.*}.ps"                     # remove temporary .ps
done

```

check it first before deploying on your whole pdf collection

EDIT: too late :D

---

