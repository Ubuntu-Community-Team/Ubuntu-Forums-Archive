---
title: "strange creation of symbolic links"
date: 2010-07-13
forum: General Help
---

### Post by m03hr3 on 2010-07-13
Hi,

what I try to do is to overwrite an existing symbolic link on Ubuntu 10.04:

```

mkdir test1
mkdir test2
ln -s test1 foo                  // (1) 
``` afterwards I have the following (expected) contents in the directory listing:

```

lrwxrwxrwx 1 root root    5 2010-07-13 10:22 foo -> test1
drwxr-xr-x 2 root root 4096 2010-07-13 10:21 test1
drwxr-xr-x 2 root root 4096 2010-07-13 10:21 test2
```Now I try to force ln (-f) to overwrite the previous created link "foo",

```
ln -sf test2 foo                //(2) 
```and afterwards the link "foo" still points to "test1" but within the dir "test1" there is:
```
lrwxrwxrwx 1 root root    5 2010-07-13 10:27 test2 -> test2
```a symbolic link named "test2". I thought command (2) would simply overwrite the previous created link "foo". Is this expected behaviour? How can I overwrite an existing symbolic link?

Thx in advance for any suggestions!

---

### Post by gmargo on 2010-07-13
Read the fine man page for **ln(1)**.  The option you are looking for is "-n" (--no-dereference).

---

### Post by m03hr3 on 2010-07-13
you are right ... sry for not RTFM :(
```

ln -snf test2 foo

```
solved the problem

---

