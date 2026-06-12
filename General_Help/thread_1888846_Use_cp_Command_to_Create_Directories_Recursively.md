---
title: "Use cp Command to Create Directories Recursively"
date: 2011-11-30
forum: General Help
---

### Post by dodle on 2011-11-30
Is there a way to get the cp command to create directories if they don't exist without having to use mkdir beforehand? I haven't found anything in the manpages and I'm guessing it's not possible.

```
$ sudo cp man/myman.1.gz /usr/local/share/man/man1/myman.1.gz
cp: cannot create regular file `/usr/local/share/man/man1/myman.1.gz': No such file or directory
```

---

### Post by drmrgd on 2011-11-30
No, you can't make a directory with cp if it doesn't exist.  About the only thing you can do is to string something together into a one liner:

```
mkdir test && cp testfile test/testfile
```

---

