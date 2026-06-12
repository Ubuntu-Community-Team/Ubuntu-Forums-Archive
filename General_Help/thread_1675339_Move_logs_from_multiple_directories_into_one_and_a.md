---
title: "Move logs from multiple directories into one and avoid name collisions"
date: 2011-01-25
forum: General Help
---

### Post by DeadWolf on 2011-01-25
What I need to do is gather a bunch of log files from various directories and move them into one spot. Below shows the directory structure.
> dir1
-a.log
-b.log
-c.log
dir2
-a.log
-b.log
-c.log
...
dirn
-a.log
-b.log
-c.log

Copying them into one directory isn't the problem. I have multiple a.log in different directories that clash when I try to copy.

Here is the shell script I have so far.
```
#!/bin/sh
tempdir=/home/user/temp
cd /home/user/logs
for file in $( find ./ -name \*.log ); do
	newfile= echo $file | sed -e 's/\.\///'
	nfile= echo $newfile | sed -e 's/\//\_/g'
	cp $file $tempdir/$nfile
done
```

It looks fine on paper but the second sed doesn't seem to work for me. It should take dir1/a.log and change is to dir1_a.log.

Any help with this would be greatly appreciated. :D

Thanks,
Keith

---

### Post by DeadWolf on 2011-01-25
I need to learn bash better. Below works great in case anyone else was having the same problem as me.

```
#!/bin/sh
tempdir=/home/user/temp
cd /home/user/log
for file in $( find ./ -name \*.log ); do
	newfile=`echo $file | sed -e 's/\.\///'`
	nfile=`echo $newfile | sed -e 's/\//\_/g'`
	cp $file $tempdir/$nfile
done
```

---

### Post by pl@yer on 2011-01-25
Just a quick hint to avoid future trouble. If you put quotes around your string variables you wont get into trouble if you have a file with spaces in the name.
```

cp "$file" $tempdir/"$nfile"

```

---

### Post by efflandt on 2011-01-25
Actually **/bin/sh** is **dash** (not bash).  So if you ever need to do something bash specific, you either need to use /bin/bash instead of /bin/sh, or read **man dash**.

Did you just have wrong directory name (log vs. logs), or did you need backticks to return the result of commands instead of assigning the command string to variables.

---

### Post by DeadWolf on 2011-01-25
Thanks for the tip pl@yer but I'm still having the white space issue. It seems to be in the loop. When I echo $file I get 2 results for the spaced filename.

Such as "file name.log" would give me "file" and "name.log".

Edit:

I found a snippet to fix that. You have to change the $IFS so it doesn't delimit white spaces.

Here is my final script
```
#!/bin/bash
SAVEIFS=$IFS
IFS=$(echo -en "\n\b")
for f in *
do
  echo "$f"
done
tempdir=/home/user/temp
cd /home/user/log
for file in $( find ./ -name \*.log ); do
	newfile=`echo "$file" | sed -e 's/ //g'`
	nfile=`echo "$newfile" | sed -e 's/\.\///'`
	n2file=`echo "$nfile" | sed -e 's/\//\_/g'`
	echo "$file"
	cp "$file" "$tempdir"/"$n2file"
done
IFS=$SAVEIFS
```

Thanks for all the help! :)

---

