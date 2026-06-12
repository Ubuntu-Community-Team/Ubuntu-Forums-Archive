---
title: "Random filename in bash script"
date: 2009-11-08
forum: General Help
---

### Post by pmooney78 on 2009-11-08
I'm teaching myself bash scripting and want to write a script that saves data to a unique filename in a certain directory. I don't care what the filename is ... I just want to make sure that I'm not overwriting existing files in that directory. is there some way to accomplish this? I can't figure anything out.

Thanks in advance.

---

### Post by mo.reina on 2009-11-08
```
#!/bin/bash

selection=
until [ "$selection" = "0" ]; do
	echo -n "enter name of file: "
	read file_name	
	if [ -f $file_name ]; then
		echo "file name exists, please choose another"
	else
		selection=0
	fi
done

echo "this is a unique file name" > $file_name
```

just replace the last line with whatever data you want to write to the file name

---

### Post by stderr on 2009-11-08
Depends how much you care about it... If it's a tiny project just for you, I might be tempted just to use date/time and then do a test to verify that it doesn't already exist in the current dir. e.g.:

```
DATETIME=$(date +%d%m%g%H%M%S)
while [ -e $DATETIME ] 
do
  DATETIME=$(date +%d%m%g%H%M%S%N)
done
```

(don't know if this works or has considered all the problems; needs testing)

---

### Post by mo.reina on 2009-11-08
didn't think of that, much simpler solution than mine

---

### Post by lswb on 2009-11-08
You also might be interested in the command 'mktemp' which creates a unique filename. (actually it creates a filename with a common part and a unique suffix, depending on the options and arguments you supply)

See "man mktemp" for details.

---

### Post by pmooney78 on 2009-11-11
One of those should work. Thanks a lot!

---

