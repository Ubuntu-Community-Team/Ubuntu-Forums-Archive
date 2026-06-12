---
title: "Deleting folders in script not working"
date: 2010-10-12
forum: General Help
---

### Post by xzased on 2010-10-12
Hi, I have the following script to delete some folders from a text file:


```
#!/bin/bash

current_dir=$(pwd)


for folder in `cat dir_list.txt`; do

echo "Processing directory "$folder

rm -rf ${current_dir}/${folder} &

wait

if [[ -d $current_dir/$folder ]]; then

echo "Failed to delete "$folder
echo ""

else

echo "Successfully deleted "$folder
echo ""

fi

done
```

This does not work. If I delete them manually it works fine, but in the script it just finishes quickly. When the variables are echoed they display the values correctly. Can someone help me out?

---

### Post by stee1rat on 2010-10-12
just tested it, and it works.

are you sure there is dir_list.txt file with a list of folders that should be deleted?

---

### Post by xzased on 2010-10-12
these are the contents of dir_list.txt:

```
2900/2901
5m00/5m09
wz00/wz01
ld00/ld30
jh00/jh15
4500/4502
8l00/8l08
md00/md08
```

so Im in the directory /home/mydir when I execute the script. mydir contains  folder 5m00 which contains a subfolder 5m09. the same for the rest of the folders...

---

### Post by stee1rat on 2010-10-12
Still works for me.. are you sure it's 00 in 5m00 and not OO? :)

Can you put the output of **du -la** and **cat dir_list.txt** here? And the output of script executing.

---

### Post by xzased on 2010-10-12
Nevermind folks, I found out what was wrong, Im still using bash 3.2, it has some issues with parsing and others that prevent it from working. Thanks for your help though, now I can confirm it works on other systems.

---

