---
title: "help with using gcc man pages"
date: 2009-10-13
forum: General Help
---

### Post by honey toast on 2009-10-13
Hi, I'm very new to man pages. I don't know what the heck I'm supposed to be looking for in all of the text. Is there a way for me to skip pages? Hot keys possibly that you can share with me?  I really want to learn how to use these man pages, and I know it will take some time. I'm building programs in C, and so how do I enable the "-wall"? do I just type -wall into the terminal and presto? Some directions for this would be appreciated. thank you

---

### Post by QIII on 2009-10-13
In the terminal

```
man gcc > gccman
```should save a text file named gccman in your home directory.  You can read it without paging down or print it or whatever, search for text...

---

### Post by OrangeVixen on 2009-10-14
The -Wall (not -wall, the W is uppercase) is an argument that you type along with gcc to compile a source and tell gcc to print all warnigs.

# gcc -Wall myprogram.c -o myprogram

Also, you can add the -g argument to compile in debugging stuff.

---

### Post by andrew.46 on 2009-10-14
Hi honey toast,

> **honey toast said:**
>  I really want to learn how to use these man pages, and I know it will take some time.

By default man pages are read using *less* although this can be changed on the commandline. So if you are keen to learn more about how to navigate man pages believe it or not you should read the man pages for *less* :). One little snippet though, if you were searching for *foo* in a man page you would type:

```
/foo
```

and then press the* n* key to search for more occurrences of *foo*.

All the best,

Andrew

---

