---
title: "tar.gz file instal"
date: 2011-03-16
forum: General Help
---

### Post by thomastt37 on 2011-03-16
installation of tar.gz files in ubuntu 10.04 and 10.10 is there a tutorial plse

michael:(

---

### Post by Grenage on 2011-03-16
First you'll want to extract the file, which you can do using the GUI or a terminal.  There will almost certainly be a readme file, and you'll almost certainly want to read it.

Now assuming that you've got source code from the tarball, you'll probably want to compile it:

```
sudo apt-get install build-essential
```

That will ensure that the compilation tools you may need are installed.  Then, from the directory you extracted the files to:

```
./configure
make
sudo make install
```

Any instructions given in the readme file will obviously be more pertinent and correct than anything I've written; make sure you're read it.

---

### Post by Script Warlock on 2011-03-16
same as above :)

---

### Post by Script Warlock on 2011-03-16
*double post*

---

### Post by iiiears on 2011-03-16
To uncompress them, execute the following command(s) depending on the extension:
$ tar zxf file.tar.gz
$ tar zxf file.tgz
$ tar jxf file.tar.bz2
$ tar jxf file.tbz2

Now change directory
$ ls
$ cd path-to-software/

Best Wishes

---

