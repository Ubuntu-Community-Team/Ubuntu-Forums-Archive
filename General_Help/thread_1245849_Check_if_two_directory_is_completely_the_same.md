---
title: "Check if two directory is completely the same"
date: 2009-08-21
forum: General Help
---

### Post by siuchi on 2009-08-21
I have backup something(its around 60GB) from another machine. 

I wanna know if there methods that i can sure the backup is completely the same as source.

Thanks a lot

---

### Post by bchurchill on 2009-08-21
For individual files you can do

```

md5sum <file1>
md5sum <file2>

```and compare the results to see if they're identical.  So one approach would be to run the md5sum on every file in each folder and compare those.  so inside folder A you could execute

```

find | xargs -n1 md5sum > ../folderA.out

```and inside folder B you could execute

```

find | xargs -n1 md5sum > ../folderB.out

```folderA.out and folderB.out will have a list of every file in each folder, along with the corresponding md5sum value.   Then run:

```

diff /path/to/folderA.out /another/path/to/folderB.out

```diff tells you the difference between two files, so if it has no output, then the two folders are identical.  If it's not identical, it will tell you exactly which files are different.

_*I've only briefly tested this*_,  but it should work fine.

Let me know if this works for you!

---

### Post by siuchi on 2009-08-21
Hi Thanks for the reply.

But what is the different between xargs -n2 and xargs -n1 ??

Thanks

---

### Post by DaithiF on 2009-08-21
Hi,
you can also use diff to compare two directories directly -- it will report any files which differ, and any files in one but not in the other.  So if you are backing up entire directories then you could do:
```
diff -q sourcedir backupdir
```
(-q reports only whether or not there are differences, it doesn't also output the differing contents, since you wouldn't want that extra detail in this case.).

---

### Post by bchurchill on 2009-08-21
@siuchi: that was my mistake.  Both should be -n1.  This tells md5sum to evaluate only one file at a time.

However, DaithiF clearly has a much nicer solution... and diff is cooler than I thought.

---

### Post by stinger30au on 2009-08-21
sudo apt-get install gnome-commander

it will do it standing on its head

[http://www.nongnu.org/gcmd/](http://www.nongnu.org/gcmd/)

---

