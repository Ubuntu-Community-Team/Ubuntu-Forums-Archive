---
title: "Script help to move files"
date: 2010-10-20
forum: General Help
---

### Post by Cyked on 2010-10-20
I'm trying to write a script to move files from one location to another, but I'm not very good at doing this.

I've done some other scripts by finding things online and changing them a bit to make them work for me.

I've made some scripts to use xargs to rm all jpg files, or something like this to tar files:

```
find . -type f -name "*.jpg" | xargs tar zcf motion.$(date +%Y%m%d-%H%M%S).tgz
```

Right now I'm trying something like this to move the files

```

#!/bin/bash
cd "/var/www/motion" || exit
ls *.avi | xargs mv /media/disk80

```

I'm guessing from the messages I'm seeing I need to write the script so it will do something like get the original file name and move it to /new/location/original_filename (if that makes sense).

If I use cp I get this: cp: omitting directory `/media/disk1'
If I use mv I get this: mv: cannot overwrite non-directory `01-20101020091317.avi' with directory `/media/disk1

I want to take existing avi files from /var/www/motion and move them to another disk /media/disk1.


Thanks!

---

### Post by sisco311 on 2010-10-20
The default syntax of mv is:
```
mv SOURCE... DEST
```

So when you run:
```
ls *.avi | xargs mv /media/disk80
```
you try to mv /media/disk80 1.avi 2.avi and so on to nnn.avi. 

If you want to use xargs, you have to specify that /media/disk80 is the DEST:
```
ls *.avi | xargs mv **-t** /media/disk80
```

But you don't have to use xargs:
```
mv *.avi /media/disk80
```

---

### Post by Cyked on 2010-10-20
That was simple enough.  I thought I remembered trying something that simple, but apparently not.

Thanks!

---

### Post by sisco311 on 2010-10-20
You're welcome!

Don't forget to mark this thread as **[SOLVED]**.

At the top of the page, click the "[COLOR="Red"]Thread Tools[/COLOR]" menu, then "Mark this thread as Solved".

Thanks.

---

