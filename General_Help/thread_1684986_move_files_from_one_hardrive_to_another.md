---
title: "move files from one hardrive to another"
date: 2011-02-10
forum: General Help
---

### Post by nikhil.deshmukh on 2011-02-10
hi can anyone guide me to copy a list of files
which has some unique string e.g 
filename_1dec_2010.tar
filename_2dec_2010.tar
filename_3dec_2010.tar
filename_4dec_2010.tar

and i have another secondary hardisk 

i guess i need to grep with "_2010" and move 
can anyone give me the command for this ?

---

### Post by Sazhen86 on 2011-02-10
Hi

You could just use cp with a wildcard:

$ cp *_2010.tar <destination>

Cheers

---

### Post by Old *ix Geek on 2011-02-10
> **nikhil.deshmukh said:**
> hi can anyone guide me to copy a list of files
which has some unique string e.g 
filename_1dec_2010.tar
filename_2dec_2010.tar
filename_3dec_2010.tar
filename_4dec_2010.tar

and i have another secondary hardisk 

i guess i need to grep with "_2010" and move 
can anyone give me the command for this ?
You've referred to both **copying** and **moving** the files. Since I'm not sure which you actually want, I'll give you an example for copying. This is a good, safe way of doing it even if you're interested in moving them, because this way you can check the new location FIRST before deleting the files from the old location, just to be sure everything got transferred as intended.

Assuming you're in the directory that holds the files:
```
for file in *_2010*
do cp -pv $file /NEW_LOCATION
done
```

With the verbose [-v] option, you'll see each file's name as it's being copied, and each file's attributes will be preserved [-p].

---

### Post by asmoore82 on 2011-02-10
The `find` command can find/gather the files for you.
It can be paired with the `xargs` command to build a move command.

The finer points to know here are: you **need** to use the
`-print0` option to `find` and the `-0` option to `xargs` - this
pairs them up to exchange the filenames is a null byte delimited format,
so that special characters in filenames such as spaces won't break the
process; you **need** to use the `-t` option to `mv` - this allows
you to specify the *target* directory to move the files to -
this is necessary because `xargs` will only append the filenames to be
moved to the end of the command.

Something like this should do the trick:
```
find */search/directory* -iname "*_2010*" -print0 | xargs -0 mv -iv -t */target/directory/*
```

---

### Post by nikhil.deshmukh on 2011-02-10
Thank you asmoore82 and all for your responses it worked

Actually i am planning to put this folder to a secondary hardisk
is it possible still to copy or move the files in the same way ?

---

### Post by Sazhen86 on 2011-02-10
Hi

To copy to an external drive you just need to know where it is mounted.  Ubuntu usually mounts external drives under /media, so if your drive is labeled mydrive you would find it under /media/mydrive and you would use /media/mydrive as the destination for the command.  Of course, you can make subfolders in /media/mydrive as well.

Cheers

---

### Post by nikhil.deshmukh on 2011-03-04
thanks a lotttttttt everyone

---

