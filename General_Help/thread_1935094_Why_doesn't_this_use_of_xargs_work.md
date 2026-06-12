---
title: "Why doesn't this use of xargs work?"
date: 2012-03-03
forum: General Help
---

### Post by Thorsen V on 2012-03-03
I was looking for a way to copy regular files that have been modified in the last couple of minutes in  my firefox cache and I came up with this (run from a terminal in the root of the firefox cache):

```
$ find . -type f -mmin +0  -mmin -2 | grep -v _CA | sed 'p;s/.*\//\~\/tmp\//'| xargs -n2 cp

cp: cannot create regular file `~/tmp/7BCC8d01': No such file or directory
cp: cannot create regular file `~/tmp/30CDDd01': No such file or directory
cp: cannot create regular file `~/tmp/42C08d01': No such file or directory

```as you can see something odd is going on.
However this appears to be okay:

```
$ find . -type f -mmin +0  -mmin -2 | grep -v _CA | sed 'p;s/.*\//\~\/tmp\//'| xargs -n2 echo "cp"
cp ./5/D7/7BCC8d01 ~/tmp/7BCC8d01
cp ./5/69/30CDDd01 ~/tmp/30CDDd01
cp ./0/7C/42C08d01 ~/tmp/42C08d01

```So I just copied the text and pasted it back into the shell, et voilà

So I'm left wondering why the direct method fails ...

---

### Post by diesch on 2012-03-03
~ doesn't have a special meaning for cp (and most other programs), it needs to get expanded by the shell to refer to your home folder.

---

### Post by Thorsen V on 2012-03-03
TY diesch

```
find . -type f -mmin +0  -mmin -10 | grep -v _CA | sed 'p;s/.*\//\/home\/thorsen\/tmp\//'| xargs -n2 cp

```works :)

---

