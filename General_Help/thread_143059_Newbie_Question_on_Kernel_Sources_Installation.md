---
title: "Newbie Question on Kernel Sources Installation"
date: 2006-03-11
forum: General Help
---

### Post by Dauphinfay on 2006-03-11
Please bare with me. I am trying to configure DRI on a thinkpad t20. Part of the process involves installing the kernel sources. I have used apt-get to download this file: linux-source-2.6.12.tar.bz2

Now what?

---

### Post by hw-tph on 2006-03-11
[b]cd /usr/src
tar xfvj linux-source-2.6.12.tar.bz2[/b]

Make sure there is a symbolic link called "linux" in /usr/src that points to the actual directory (with version numbers).


Håkan

---

### Post by Dauphinfay on 2006-03-11
how do I create that symbolic link? Also, uname -r gives me this:

2.6.12-10-386


now that doesn't match what was downloaded as you can see. Is this normal from ubuntu?

---

### Post by hw-tph on 2006-03-11
You create symbolic links using the ln command, with the -s option.
[b]cd /usr/src
ln -s linux-2.6-*version* linux[/b]

Verify the link using **ls -l**:
```
hakan@devon:/usr/src$ ls -l linux
lrwxrwxrwx  1 hakan src 13 2006-02-24 13:12 linux -> linux-2.6.15//
hakan@devon:/usr/src$
```


Håkan

---

### Post by Dauphinfay on 2006-03-12
After creating the symbolic link using ln -s linux-source-2.6.12, I am still unable to run mrproper. Am I missing something?

---

