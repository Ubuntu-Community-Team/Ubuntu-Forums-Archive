---
title: "Shell scripting, renaming many files. I have searched the forums (plz don't ignore)"
date: 2011-01-22
forum: General Help
---

### Post by Photon_Wangler on 2011-01-22
What I need is a shell script to rename all the files inside of any directory without regard of their names.
For example a folder has eight files with the names:

IMG_0001.jpg
img_002.jpg
ImG_0005.jpg
IMG_0009.JPg
IMG_009.JPg
IMG_00009.JPg
IMG_9.JPg
IG_0009.JPg

I want to rename them to IMG_1.jpg,  IMG_2.jpg,  IMG_3.jpg,  IMG_4.jpg... IMG_8.jpg.

A solution would cease my hair pulling.  ;)

---

### Post by Vaphell on 2011-01-22
```
#!/bin/bash

dir="."
if [ "$1" ]; then dir="$1"; fi
echo Directory: $dir

# temporary names with __ prefix
# to avoid collision with existing files
echo Stage 1 
i=0
for file in "$dir"/*.[jJ][pP][gG]
do
  i=$((i+1))
  echo "$file" "=>" "$dir"/__img_$i.jpg
  mv   "$file"      "$dir"/__img_$i.jpg
done

# rename temporary files to their final name
echo Stage 2
for file in "$dir"/*.jpg
do
  echo "$file" "=>" "$dir"/${file#*__}
  mv   "$file"      "$dir"/${file#*__}
done
```

test it on some dummy data set first, even with some nasty combination of spaces in filenames and directory names and see if the file count is ok (no file gets eaten in the process). I wouldn't want to destroy your collection by some oversight

by default it assumes current dir ., but you can pass a parameter
```
script some_dir
``` (i didn't bother with checking if the dir name is trailed by / or not, script assumes that there is no trailing /)

---

### Post by Photon_Wangler on 2011-01-22
Thank you so much, the script does exactly what I needed. Now I can integrate it into my image capture script.
:popcorn:

---

