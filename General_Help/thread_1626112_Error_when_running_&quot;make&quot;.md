---
title: "Error when running &quot;make&quot;"
date: 2010-11-19
forum: General Help
---

### Post by cats4gold on 2010-11-19
Today, I was trying to compile and install a minecraft mapper with the program "make". I navigated to the directory in terminal and ran make. It found the make file and begins to work, then spits an error and stops. To be specific, this was the error:

```
cats4gold@computer:~/Downloads/cartograph-linux$ make
make -C src/
make[1]: Entering directory `/home/cats4gold/Downloads/cartograph-linux/src'
g++ -c -pipe -O2 -Wall main.cpp -o main.o
In file included from main.cpp:16:
Level.h:8: fatal error: zlib.h: No such file or directory
compilation terminated.
make[1]: *** [main.o] Error 1
make[1]: Leaving directory `/home/cats4gold/Downloads/cartograph-linux/src'
make: *** [default] Error 2
cats4gold@computer:~/Downloads/cartograph-linux$
```

It just looks like a missing directory, but I was just making sure this was all. Thanks in advance.

---

### Post by mr_luksom on 2010-11-19
Have you got the 'build-essential' package?

```
 sudo apt-get install build-essential 
```

You should have this before compiling.

---

### Post by SeijiSensei on 2010-11-19
No, it can't find the zlib.h header file; zlib provides support for the gzip compression algorithm.

I'm going to guess that you don't have the kernel-headers installed; that's where zlib.h lives in my installation.  The package name depends on your version of Ubuntu.  Try running "dpkg -s linux-headers-$(uname -r)" to see if you have the headers installed.  If not, then use "sudo apt-get install linux-headers-$(uname -r)" to get them.

---

### Post by cats4gold on 2010-11-19
> **SeijiSensei said:**
> No, it can't find the zlib.h header file; zlib provides support for the gzip compression algorithm.

I'm going to guess that you don't have the kernel-headers installed; that's where zlib.h lives in my installation.  The package name depends on your version of Ubuntu.  Try running "dpkg -s linux-headers-$(uname -r)" to see if you have the headers installed.  If not, then use "sudo apt-get install linux-headers-$(uname -r)" to get them.Status: install ok installed

> **mr_luksom said:**
> Have you got the 'build-essential' package?

```
 sudo apt-get install build-essential 
```

You should have this before compiling.
build-essential is already the newest version.

---

### Post by cats4gold on 2010-11-19
> **SeijiSensei said:**
> No, it can't find the zlib.h header file; zlib provides support for the gzip compression algorithm.

I'm going to guess that you don't have the kernel-headers installed; that's where zlib.h lives in my installation.  The package name depends on your version of Ubuntu.  Try running "dpkg -s linux-headers-$(uname -r)" to see if you have the headers installed.  If not, then use "sudo apt-get install linux-headers-$(uname -r)" to get them.
Actually, it appears they weren't installed, or at least needed to be updated. No effect, though.

---

### Post by SeijiSensei on 2010-11-19
[http://manpages.ubuntu.com/manpages/maverick/man3/zlib.3.html](http://manpages.ubuntu.com/manpages/maverick/man3/zlib.3.html)

---

### Post by mc4man on 2010-11-19
Do you have zlib1g-dev installed?

Edit: if not then install the ubuntu package, (sudo apt-get install zlib1g-dev ), do not do as this fellow (built and installed zlib source
[http://ubuntuforums.org/showthread.php?p=10121928#post10121928](http://ubuntuforums.org/showthread.php?p=10121928#post10121928)

---

### Post by cats4gold on 2010-11-20
> **mc4man said:**
> Do you have zlib1g-dev installed?

Edit: if not then install the ubuntu package, (sudo apt-get install zlib1g-dev ), do not do as this fellow (built and installed zlib source
[http://ubuntuforums.org/showthread.php?p=10121928#post10121928](http://ubuntuforums.org/showthread.php?p=10121928#post10121928)
Thanks! That solves one problem, but leads to another error:
```
cats4gold@computer:~/Downloads/cartograph-linux$ make
make -C src/
make[1]: Entering directory `/home/cats4gold/Downloads/cartograph-linux/src'
g++ -c -pipe -O2 -Wall main.cpp -o main.o
g++ -c -pipe -O2 -Wall Level.cpp -o Level.o
Level.cpp:2: fatal error: png.h: No such file or directory
compilation terminated.
make[1]: *** [Level.o] Error 1
make[1]: Leaving directory `/home/cats4gold/Downloads/cartograph-linux/src'
make: *** [default] Error 2
cats4gold@computer:~/Downloads/cartograph-linux$ 

```

Same thing, different missing file.

---

### Post by mc4man on 2010-11-20
What you can do is search here for the file and ck. the results (scroll down to "Search the contents of packages"
Make sure you set to search the ubuntu release you're using, 
[http://packages.ubuntu.com/](http://packages.ubuntu.com/)
Ex.
these are the results on maverick for png.h
[http://packages.ubuntu.com/search?searchon=contents&keywords=png.h&mode=exactfilename&suite=maverick&arch=any](http://packages.ubuntu.com/search?searchon=contents&keywords=png.h&mode=exactfilename&suite=maverick&arch=any)

So I'd take a guess and install 'libpng12-dev'

Edit: which mapper are you trying to build?

---

### Post by cats4gold on 2010-11-20
> **mc4man said:**
> What you can do is search here for the file and ck. the results (scroll down to "Search the contents of packages"
Make sure you set to search the ubuntu release you're using, 
[http://packages.ubuntu.com/](http://packages.ubuntu.com/)
Ex.
these are the results on maverick for png.h
[http://packages.ubuntu.com/search?searchon=contents&keywords=png.h&mode=exactfilename&suite=maverick&arch=any](http://packages.ubuntu.com/search?searchon=contents&keywords=png.h&mode=exactfilename&suite=maverick&arch=any)

So I'd take a guess and install 'libpng12-dev'

Edit: which mapper are you trying to build?
I'll take a look at these, thanks!

Also, I'm working on cartograph.

---

### Post by cats4gold on 2010-11-20
Make ran succesfully and placed an executable in the folder named "cartograph"

When I right click and press open; no response. Do I need to open it from the terminal?

---

### Post by cats4gold on 2010-11-20
Yes, I did. Okay, problem solved. Thanks everyone!

---

