---
title: "[extremely beginner] - installing SIP?"
date: 2010-06-05
forum: General Help
---

### Post by _Block_ on 2010-06-05
I need to install this so I can install pyQT4, so I downloaded the .tar.gz, unpacked, ran configure.py, then sudo make, sudo make install, but I get this error on the last steps (also, I checked the installation instruction when after I did all this, and it is the same)

g++  -o sip main.o transform.o gencode.o export.o heap.o parser.o lexer.o 
make[1]: g++: Command not found
make[1]: *** [sip] Error 127
make[1]: Leaving directory `/home/xxx/xxxxx/sip-4.10.2/sipgen'
make: *** [all] Error 2

so I thought okay why are they using the command g++ instead of gcc? I did a:  cat * | grep g++ to find where they had put g++ and correct in but there's too many places, usually in places if I edited it it looks like it would stuff up.


Any help?

EDIT: I found a package for it in the repos, that worked out fine.

---

### Post by harrisonk on 2010-06-05
Hello

In line 2 it says: "make[1]: g++: Command not found" is g++ (what it is trying to use) installed? try that.

The install command is:

```
 sudo apt-get install g++ 
```Harrison

---

### Post by _Block_ on 2010-06-05
> **harrisonk said:**
> Hello

In line 2 it says: "make[1]: g++: Command not found" is g++ (what it is trying to use) installed? try that.

The install command is:

```
 sudo apt-get install g++ 
```Harrison

Alright, that gets rid of the first error, now I have thousands of errors when I try to make/make install:

[http://paste.pocoo.org/show/222392/](http://paste.pocoo.org/show/222392/)

---

### Post by harrisonk on 2010-06-06
[SIZE=2]Hello

It looks as though there are errors in the *.c and *.py files but at the end of the errors that you need to include sudo as in:

```
 sudo install && sudo make install 
```

Try re-downloading the files and if you get the same errors try running the make commands with sudo.

Harrison
[/SIZE]

---

### Post by sffvba[e0rt on 2011-09-24
Back to sleep thread...


404

---

