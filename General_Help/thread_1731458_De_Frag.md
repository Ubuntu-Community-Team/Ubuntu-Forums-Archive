---
title: "De Frag"
date: 2011-04-17
forum: General Help
---

### Post by JACKONFIRE1888 on 2011-04-17
Is it possible to run a De-frag in Ubuntu and if so where is it?

I have noticed when I try to open game sites and facebook that the screen goes grey and seems to struggle to load, I have used less than 13% of the memory, but perhaps a clean up would help.:confused:

---

### Post by TeoBigusGeekus on 2011-04-17
> **JACKONFIRE1888 said:**
> Is it possible to run a De-frag in Ubuntu and if so where is it?

I have noticed when I try to open game sites and facebook that the screen goes grey and seems to struggle to load, I have used less than 13% of the memory, but perhaps a clean up would help.:confused:

No need for defragmentation in linux.
Your problems are probably flash related - how about cpu usage?

---

### Post by cottfcfan on 2011-04-17
No need to defrag in Linux.
Your problem could be Graphics card related.
Are you using the open source drivers or proprietary ones?

---

### Post by oklokl on 2011-04-17
[http://www.webupd8.org/2009/10/defragmenting-linux-ext3-filesystems.html](http://www.webupd8.org/2009/10/defragmenting-linux-ext3-filesystems.html)


[http://vleu.net/shake/](http://vleu.net/shake/)


```
fdisk -l

sudo shake --old 0 --bigsize 0 /dev/sda1 
```Usage: shake [OPTION]... [FILE|DIRECTORY]...
Rewrite fragmented or misplaced files, maybe improving performance.
Reads file list from standard input if there is no files in the arguments.
You have to mount your partition with the user_xattr option.

  -c, --max-crumbc    max number of crumbs
  -C, --max-fragc    max number of fragments
  -d, --max-deviance    max distance between file start and it's ideal position
  -h, --help        you're looking at me !
  -L, --no-locks    don't put a lock on written files
  -m, --many-fs        shake subdirectories that are on different filesystems
  -n, --new        age of "new" files, which will be shak()ed
  -o, --old        age of "old" files, which won't be shak()ed
  -p, --pretend        don't alter files
  -r, --crumbratio    ratio of the file under which a fragment is a crumb
  -s, --smallsize    the size under which a file is considered small
  -S, --bigsize        the size under which a file is considered big
  -t, --small-tolerance    multiply crumbratio and divide maxfnumber of small files
  -T, --big-tolerance    multiply crumbratio and divide maxfnumber of big files
  -v, --verbose        increase the verbosity level
  -V, --version        show version number and copyright
  -X, --no-xattr    disable usage of xattr
Report bugs to <brice.arnould+shake@gmail.com> or at
[http://savannah.nongnu.org/projects/shake](http://savannah.nongnu.org/projects/shake)

---

### Post by JACKONFIRE1888 on 2011-04-17
Thank You all for your quick advice, I will now get a friend to translate it into some thing this Idiot can understand.

---

