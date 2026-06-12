---
title: "Copy, skip files"
date: 2011-06-30
forum: General Help
---

### Post by jaes84 on 2011-06-30
How would i go about copying files to a directory, yet skip the files that already exist in the directory, and also remove the files that are in the directory.

For example:
```

$ls /dir1
img001.jpg
img002.jpg
img003.jpg
$ls /dir2
img001.jpg
img002.jpg

```Now i would like to copy from dir1 to dir2, but the contents of dir2 would be:
```

$ls /dir2
img003.jpg

```This is just an example, but how would i go about doing this?

---

### Post by jaes84 on 2011-06-30
Would this work?
```

rsync --exclude '/`ls /dir2`'

```

---

### Post by evilsoup on 2011-06-30
To copy files without overwriting destination files of the same name, use

```
cp -n dir1/*.jpg dir2/
```

I suspect to get what you want would require a script. Try:

```

#!/bin/bash
ls dir2 > .tempfile
dir1=$1
dir2=$2
cp -n $dir1 $dir2/
linecount=wc -l .tempfile | awk '{print $1}'
countline=1
cd dir2
until [ "$countline" -gt "$linecount" ]; do
foo=`head -$countline .tempfile | tail -1`
rm foo
countline=$((countline+1))
done
rm .tempfile
exit

```

Save it in you bin (~/bin) as copykill, set as executable. To use it type ```
copykill /dir1/*.filetype /dir2/
```

USE WITH CAUTION, that script as written will remove EVERYTHING that used to be in the directory (except directories).

---

### Post by jaes84 on 2011-06-30
> **evilsoup said:**
> To copy files without overwriting destination files of the same name, use

```
cp -n dir1/*.jpg dir2/
```I suspect to get what you want would require a script. Try:

```

#!/bin/bash
ls dir2 > .tempfile
dir1=$1
dir2=$2
cp -n $dir1 $dir2/
linecount=wc -l .tempfile | awk '{print $1}'
countline=1
cd dir2
until [ "$countline" -gt "$linecount" ]; do
foo=`head -$countline .tempfile | tail -1`
rm foo
countline=$((countline+1))
done
rm .tempfile
exit

```Save it in you bin (~/bin) as copykill, set as executable. To use it type ```
copykill /dir1/*.filetype /dir2/
```USE WITH CAUTION, that script as written will remove EVERYTHING that used to be in the directory (except directories).
Thanks alot, however when i try to run this script exactly as you said, i get this
```

rm: cannot remove `foo': No such file or directory
/bin/copykill: line 9: [: : integer expression expected
head: cannot open `.tempfile' for reading: No such file or directory

```

Also, when i try to run cp -n, i get this
```

cp: invalid option -- n
Try `cp --help' for more information.

```

---

### Post by sisco311 on 2011-06-30
Something like this should do the trick:
```
#!/bin/bash

shopt -s nullglob

dir1=**"/path/to/dir 1"**
dir2=**"/path/to/dir 2"**

cd "$dir1" || exit 1
for file in *.jpg
do
   if [ -f "${dir2}/$file" ]
  then
    echo "$file exists in $dir2"
    **echo** rm -- "${dir2}/$file"
  else
    echo "$file doesn't exist in $dir2"
    **echo** cp -- "$file" "$dir2"
  fi
done

```

Because of the (bold) **echo** commands it will only show which files would have been copied and removed. Delete them to actually copy and remove the files.

Also you have to replace **/path/to/dir 1** and **/path/to/dir 2** with the real path to dir1 and dir2.

---

### Post by jaes84 on 2011-06-30
> **sisco311 said:**
> Something like this should do the trick:
```
#!/bin/bash

shopt -s nullglob

dir1=**"/path/to/dir 1"**
dir2=**"/path/to/dir 2"**

cd "$dir1"
for file in *.jpg
do
   if [ -f "${dir2}/$file" ]
  then
    echo "$file exists in $dir2"
    **echo** rm -- "${dir2}/$file"
  else
    echo "$file doesn't exist in $dir2"
    **echo** cp -- "$file" "$dir2"
  fi
done

```

Because of the (bold) **echo** commands it will only show which files would have been copied and removed. Delete them to actually copy and remove the files.

Also you have to replace **/path/to/dir 1** and **/path/to/dir 2** with the real path to dir1 and dir2.
Thanks alot, that really helped.

While im at it, do you know of any sites where i could learn bash scripting?

---

### Post by sisco311 on 2011-06-30
> **jaes84 said:**
> Thanks alot, that really helped.

You're welcome!

> **jaes84 said:**
> 
While im at it, do you know of any sites where i could learn bash scripting?

Yep, the BashGuide at [http://mywiki.wooledge.org/](http://mywiki.wooledge.org/)
alongside with the BashFAQ and BashPitfalls on the same site.

and

[http://wiki.bash-hackers.org/start](http://wiki.bash-hackers.org/start)

---

### Post by jaes84 on 2011-06-30
Thanks alot, marking this thread as solved

---

