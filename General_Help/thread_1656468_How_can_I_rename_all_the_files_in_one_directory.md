---
title: "How can I rename all the files in one directory?"
date: 2010-12-30
forum: General Help
---

### Post by sofasurfer on 2010-12-30
I have many files in a directory. They all have names with a .pdf extension. How can I remane all of them so that they are named as so... 1.pdf, 2.pdf, 3.pdf? I want to do it with one command or somehow that I do not have to manually rename each one.

---

### Post by TeoBigusGeekus on 2010-12-31
```
#!/bin/bash
a=1
for i in *.pdf
do
fn=$(basename $i) 
mv $fn $a.pdf
rm $fn
let a+=1
done
```
Backup the files first cause the script deletes the original ones.

---

