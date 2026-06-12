---
title: "install rarcrack"
date: 2010-11-07
forum: General Help
---

### Post by has63 on 2010-11-07
trying to install rarcrack and don't know where to start. is there a place to get basic detailed help for such things?
     thanks
                  has63

---

### Post by Karakh on 2010-11-07
From the website:

```
$ tar -xjf rarcrack-VERSION.tar.bz2
$ cd rarcrack-VERSION
$ make
$ sudo make install
```

Is this not working? What errors are you getting?

---

### Post by Karakh on 2010-11-07
> i don't know where to type thatin

Please don't use private messages. People search the forums looking for past solutions to current problems, and PM's aren't much help to them.


If you're not comfortable using the command line, I wouldn't recommend attempting to compile and install a program from source.

There is a .deb file available **[here]("http://stebalien.googlecode.com/files/rarcrack.deb")**, and it should install just by downloading and double clicking it. 

_**Disclaimer: Deb may not work. Deb may be malicious. Deb may give you cancer... Don't blame me...**_

---

### Post by fipem on 2012-11-19
> **Karakh said:**
> From the website:

```
$ tar -xjf rarcrack-VERSION.tar.bz2
$ cd rarcrack-VERSION
$ make
$ sudo make install
```

Is this not working? What errors are you getting?

I got:

```

rulo@rulo-ubuntu:~/Downloads/rarcrack-0.2$ make
gcc -pthread rarcrack.c `xml2-config --libs --cflags` -O2 -o rarcrack
/bin/sh: 1: xml2-config: not found
In file included from rarcrack.c:21:0:
rarcrack.h:25:48: fatal error: libxml/xmlmemory.h: No such file or directory
compilation terminated.
make: *** [all] Error 1

```

And from de deb. file I got:

The file “/home/rulo/Downloads/rarcrack.deb” could not be opened.

Anny suggestions?

---

### Post by Elfy on 2012-11-19
Old thread closed.

---

