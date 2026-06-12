---
title: "archive files .zip /stored without compress"
date: 2012-04-10
forum: General Help
---

### Post by rezx on 2012-04-10
how to archive some files .zip but not compress them just stored without compress, like what i have on windows , store>fast>fastest>normal> and so one i hve lots of option when make an archive here i dont hve this options is there an _**Easy Way**_ to make a store archive i just want to collect some files to compress and encrypt it no need to compress them.

when i click right mouse and choose compress it give me options to .zip .7z and more but no options to the compress method ?

---

### Post by oldos2er on 2012-04-10
```
zip -0 foo.zip /path/to/files/foo
```

---

### Post by rezx on 2012-04-10
> **oldos2er said:**
> ```
zip -0 foo.zip /path/to/files/foo
```
i dont want any commands, i just download this[ ]("http://www.peazip.org/download-linux-gtk2-deb.html")[PeaZip ]("http://www.peazip.org/download-linux-gtk2-deb.html")but when i try to install it it says
> Error: Dependency is not satisfiable: libgdk-pixbuf2.0-0 (>= 2.21.6)

now i need one of two ways install this soft, or another way to compress but without commands ^_^

---

### Post by rezx on 2012-04-11
up :)

---

### Post by Vaphell on 2012-04-11
with nautilus-actions installed you can customize your right click menu and you would be able to make that zip -0 command cooperate from the nautilus level

run nautilus actions user interface
create new menu entry eg 'store files'
command: zip
parameters: -0 <dir>.zip <list of files>
there are many %X placeholders listed that provide various things, you need proper ones to get <dir> and <list of files>

unfortunately i can't be bothered to get it working all the way, you'd need to fill the gaps in.

---

### Post by rezx on 2012-04-11
> **Vaphell said:**
> with nautilus-actions installed you can customize your right click menu and you would be able to make that zip -0 command cooperate from the nautilus level

run nautilus actions user interface
create new menu entry eg 'store files'
command: zip
parameters: -0 <dir>.zip <list of files>
there are many %X placeholders listed that provide various things, you need proper ones to get <dir> and <list of files>

unfortunately i can't be bothered to get it working all the way, you'd need to fill the gaps in.

sure, 'll try my best... but if there any one know better way, please join :popcorn:

---

### Post by callmemahavir on 2012-04-11
Is the file already compressed ?

If the files are already compressed then compression ratio won't be good.

---

