---
title: "Unique Batch Renaming"
date: 2010-04-21
forum: General Help
---

### Post by DevHead on 2010-04-21
I've a set of photos that I would like to **randomize** their filenames by renaming them.  However when renaming them, their filename must be **unique**.

Thanks.

---

### Post by undecim on 2010-04-21
You can rename them by their MD5 sum.

The chances of any two MD5s being identical is low. Any two identical files will have the same MD5sum.

This command should rename every .jpg file in a Pictures and its subdirectories based on md5sums (I haven't tested this, so try it on a COPIED directory first.)

```
find Pictures -iname *.jpg -exec bash -c "FILE={}; mv $FILE `md5sum ${FILE%%.*} | awk '{ print $1}'`.${FILE#*.}" ;
```

---

### Post by gzarkadas on 2010-04-21
Assuming you want unique filenames for putting all photos in one directory, you could use [mktemp]("http://linux.die.net/man/1/mktemp") with a directory and template of your choice to make a file with a unique name. Then write your image there and rename it to add the extension. Do the last step _after_ creating all files, to avoid possible collisions in name.

Example code (the <...> must be supplied by you):
```

mkdir -p <dest-dir>
for file in $(ls <image-dir>/<image-pattern>); do
    img=$(mktemp -p <dest-dir> <image-prefix>.XXXXXXXXXX)
    cp $file $img
done
for file in $(ls <dest-dir>); do
    mv $file "${file}.<image-extensions>"
done

```

---

### Post by gzarkadas on 2010-04-21
Yes, the previous post has better style (and also finished earlier :)). It is also most probably faster for a large number of files. 

If you don't like the charset created by md5sum (0-9 and a-f) you can append a `tr' command to convert it to your liking. 

Also you can try sha256sum to have an even lower rate of collisions if you really have a very large number of files (though most of the time it will be a slower overkill).

---

### Post by kaibob on 2010-04-21
If you simply want to rename a bunch of JPG files with a random file name, the following will do what you want. If your want to rename files recursively, you could instead use the find command with a while-read loop. When renaming 100 or so files, there is essentially no chance that two files be given the same file name. 

```
#!/bin/bash

for file in *.jpg ; do
   name=$(tr -dc "[:alnum:]" < /dev/urandom | head -c 10)
   mv "$file" ${name}.jpg
done
```

REFERENCE
[http://aaronhawley.livejournal.com/9531.html](http://aaronhawley.livejournal.com/9531.html)

---

### Post by DevHead on 2010-04-21
Thanks for your inputs.  I will try them all. :)

---

