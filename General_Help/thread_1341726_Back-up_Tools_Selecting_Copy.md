---
title: "Back-up Tools/ Selecting Copy"
date: 2009-11-30
forum: General Help
---

### Post by zggame on 2009-11-30
Hi, I have a big folders with all my photos (~100G). The structure is like this:

-photo
 [LIST]
[*]-DATE1 
[LIST]
[*]     -LOTs of RAW files from DSLR(*.cr2,*.dng,*.pef)
[*]     -Some JPGs/AVIs from small DC
[*]     -EXPORT
       [LIST]
[*]JPGS processed from RAW files.
[/LIST]
[/LIST]
[*]   -DATE2
[/LIST]
  .....

I would like to copy all the jpg/avi files into another disk for sending to my parents without those massive raw files, which they do not care. But I would like to preserve the path structure.   

Is there any quick script that can do this?  Or is there any ready tool for such thing?  Thanks.:popcorn::popcorn:

---

### Post by kaibob on 2009-11-30
I don't know if you want full or partial paths in the target directory. If the latter, the following shell script will do what you want. You need to change the source and target directories and the path2 variable:

```
#!/bin/bash

source="/home/kaibob/photos"
target="/home/kaibob/parents"

find "$source" -iname '*.jpg' -o -iname '*.avi' -type f | while read file ; do
   path1="${file%/*}"
   path2=${path1#/home/kaibob}
   mkdir -p "${target}${path2}"
   cp "$file" "${target}${path2}"
done
```

I don't know of a ready tool that will do what you want. Perhaps with this bump, another forum member will be able to help.

---

