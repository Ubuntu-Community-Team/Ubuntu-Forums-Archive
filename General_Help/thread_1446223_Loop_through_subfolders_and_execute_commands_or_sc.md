---
title: "Loop through subfolders and execute commands or scripts"
date: 2010-04-03
forum: General Help
---

### Post by muskedear on 2010-04-03
Good Day,

Can anyone offer a suggestion?  Let's say I have 4 subfolders in the folder test as shown below:

drwxr-xr-x 2 muskedear muskedear 4096 2010-04-03 17:11 sub001_p1
drwxr-xr-x 2 muskedear muskedear 4096 2010-04-03 15:38 sub002_p1
drwxr-xr-x 2 muskedear muskedear 4096 2010-04-03 15:38 sub001_p2
drwxr-xr-x 2 muskedear muskedear 4096 2010-04-03 15:38 sub002_p2

I want to loop through the folders and check if they end with *_p1 or *p2.  If a given folder ends with *p1, I want to cd to that folder and manipulate certain files in that folder.  If the folder ends with *p2, I want to perform different manipulations on certain files.

Thanks for any insight.

---

### Post by kaibob on 2010-04-03
The following should do what you want. You have to change the target directory and replace the echo commands with whatever file manipulations you want to perform. 

Any variables set within the while-read loop are lost outside the loop. There are some easy fixes if that's an issue. 

```
#!/bin/bash

target="/home/muskedear/test"

find "$target" -type d | while read dir ; do
   if [ "${dir:(-2):2}" = p1 ] ; then
      echo "$dir is a p1 directory"
   elif [ "${dir:(-2):2}" = p2 ] ; then
      echo "$dir is a p2 directory"
   fi
done
```

---

