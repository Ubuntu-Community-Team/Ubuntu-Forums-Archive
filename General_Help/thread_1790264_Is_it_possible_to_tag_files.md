---
title: "Is it possible to tag files?"
date: 2011-06-24
forum: General Help
---

### Post by GeoffreyBernardo on 2011-06-24
In F-Spot photo manager, one can tag photos to organize them. The advantage of tags over folders is that one do not have to place a file in more than one folder if it belongs to more than one category.

Is it possible to tag files in either Nautilus or the command line shell?

---

### Post by Broshea on 2011-06-24
> **GeoffreyBernardo said:**
> In F-Spot photo manager, one can tag photos to organize them. The advantage of tags over folders is that one do not have to place a file in more than one folder if it belongs to more than one category.

Is it possible to tag files in either Nautilus or the command line shell?

Not that I am aware of.  However, if having copies of files is a matter of disk space utilization, you could always create symbolic links (or even hard links) to the file in different directories:

$ mkdir -p test/foo test/bar
$ echo "Hello Ubuntu Forums!" > test/foo/hello
$ ls -l test/foo test/bar
test/bar:
total 0

test/foo:
total 4
-rw-r--r-- 1 boshea boshea 21 2011-06-24 16:15 hello

$ cd test/bar
$ ln -s hello ../foo/hello
$ ls -l
lrwxrwxrwx 1 boshea boshea 12 2011-06-24 16:19 hello -> ../foo/hello
$ cat hello
Hello Ubuntu Forums!

---

### Post by GeoffreyBernardo on 2011-06-24
Yes, that is a good option. Thanks.

---

