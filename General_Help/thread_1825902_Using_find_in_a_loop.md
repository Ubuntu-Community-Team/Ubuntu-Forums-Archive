---
title: "Using find in a loop"
date: 2011-08-15
forum: General Help
---

### Post by kuproverto on 2011-08-15
I'm trying to write a bash script which will find files then move them to a specific directory.

So far I have:

```
#!/bin/bash

#script to find and move files

src_dir="/path/to/source/directory"
des_dir_mov="/path/to/destination/directory/for/movies"
des_dir_img="/path/to/destination/directory/for/images"

find $src_dir -iname '*.avi' -type f -exec mv '{}' $des_dir_mov ';'
```

I'd like to have all the possible movie file types then the image file types checked in a loop.

Every time I try to include an array in this script it breaks :(

Could someone help?

---

### Post by kuproverto on 2011-08-16
Instead of a loop, this works.

```
find $src_dir -regex ".*\(mov\|avi\|wmv\|flv\|3g2\|mpg\)$" -type f -exec mv '{}' $des_dir_mov ';'
find $src_dir -regex ".*\(jpg\|jpeg\|png\|gif\|psd\|bmp\|tif\)$" -type f -exec mv '{}' $des_dir_img ';'
```

---

### Post by papibe on 2011-08-18
Very nice :P  Just don't forget to quote your variables ;)
```
find "$src_dir" -regex .... "$des_dir_mov" \;

```

---

### Post by CaptainMark on 2011-08-18
i have a for loop in one script i wrote ages ago, feel free to use that as a template if you like ```
#!/bin/bash

for script in $(ls /home/mark/Documents/bash/login_scripts_desktop/*)
do
bash $script &
done
```

---

