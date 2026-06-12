---
title: "Copy files listed in a text file.... HELP!"
date: 2010-04-14
forum: General Help
---

### Post by Quint2020 on 2010-04-14
Ok so I've got a text file with a list of .gz files, these .gz files are in various sub directories of one parent directory and I've hacked this little script together to copy them from their current location to a new one and spit out any it can't find to "/home/user/not_found" but for the life of me can't get it to run properly!

Any help would be greatly appreciated.

The shell script as it currently looks:

```
#!/bin/sh

source="/mnt/source_dir"
dest="/mnt/output_dir"
list="/home/user/file_list"

while read -r line
do
  file=`find "$source" -name "$line"`
  if [ -n "$file" ]
  then
    cp $file $dest
  else
    echo "$line" >> "/home/user/not_found"
  fi
done<$list
```

---

### Post by iponeverything on 2010-04-14
```

cat file_list | awk '$1 {print "find /src_dir -type f -name "$1" -exec cp \"{}\" /dest_dir \";\""}' |sh

```

```

ls /dest_dir > outfile; cat file_list >> outfile
cat outfile | sort | uniq >> not_found

```

---

### Post by Quint2020 on 2010-04-15
Well I've finally managed to test the above solution and it looks like it doesn't work...

Anybody got any idea how to do this, the frustrating thing is that I used to have a script that did exactly this (it's what my code above is based on) only I can't find it!

---

