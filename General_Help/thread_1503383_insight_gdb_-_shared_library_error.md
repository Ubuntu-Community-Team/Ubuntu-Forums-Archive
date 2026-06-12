---
title: "insight gdb - shared library error"
date: 2010-06-06
forum: General Help
---

### Post by hacklan07 on 2010-06-06
I'm trying to use insight, a gui for gdb, but keep running into issues.  My understanding was that insight is supposed to be included with gdb itself, but typing "insight" into a terminal only resulted in the terminal reporting it did not understand the command "insight" (i have gdb and kdbg installed).  So, I installed Insight from [http://manpages.ubuntu.com/manpages/intrepid/en/man1/insight-bin.1.html](http://manpages.ubuntu.com/manpages/intrepid/en/man1/insight-bin.1.html) (because the ubuntu package manager didn't have any program by the name of insight) , but now when I try to launch Insight, the terminal throws up the error "error while loading shared libraries: libitcl3.2.so.1: cannot open shared object file: No such file or directory".  Is anyone familiar with insight?

Thanks!

(I did a google search for the error and got a bunch of links about errors while loading shared libraries, bu i wasn't sure how to go through with the reported solutions)

---

### Post by happyhamster on 2010-06-06
Try installing the itcl package:
```

sudo apt-get install itcl3

```
and perhaps itcl3-dev as well. Good luck.

---

### Post by hacklan07 on 2010-06-06
I installed both as you directed, and itcl3-dev did install a couple new files, but still get the same error when trying to launch "insight"... :-/

---

### Post by happyhamster on 2010-06-06
- It's probably this bug:
[https://bugs.launchpad.net/ubuntu/+source/insight/+bug/499602](https://bugs.launchpad.net/ubuntu/+source/insight/+bug/499602)

- To test, run:

dpkg -L itcl3 | grep ^/usr/lib/

- If it only lists libitcl3.4.so.1 you're seeing the above bug. This could likely be solved by creating a symbolic link manually. 

sudo ln -s /usr/lib/libitcl3.4.so.1 /usr/lib/libitcl3.2.so.1

- After that command, any program asking for libitcl3.2.so.1 will be redirected to libitcl3.4.so.1. I think it should be safe, because nothing default depends on libitcl3.2.so.1. Anyway, if it doesn't work, or if it breaks stuff, simply delete the link:

sudo rm /usr/lib/libitcl3.2.so.1

- Good luck.

---

### Post by hacklan07 on 2010-06-07
Alright, I ran 

sudo ln -s /usr/lib/libitcl3.4.so.1 /usr/lib/libitcl3.2.so.1

which took care of that error, but then I received almost the same error, but with the libitk3.2.so.1 file.  So, I edited the command you gave me to

sudo ln -s /usr/lib/libitk3.3.so.1 /usr/lib/libitk3.2.so.1

which took care of this second error.  Now, when I try to launch insight I receive the error "**Itcl_Init failed: version conflict for package "Tcl": have 8.4, need 8.5**".  From what I can tell from the ubuntu package manager, tcl 8.4 and 8.5 are both installed.

---

### Post by hacklan07 on 2010-06-07
doesn't seem like a good idea to uninstall tcl 8.4.  any other ideas?  Thanks!

---

### Post by happyhamster on 2010-06-07
It's broken: it depends on tcl8.4 but asks for 8.5. Debian has a bugreport on this:
[http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=582332](http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=582332)

But even worse, the insight homepage says:
> 
News
July 19, 2009:

    Updated Insight 6.8-1 available 
    Insight 6.8 has been available for some time, and the current release tarball has issues with newer versions of X11. As a result, I am making available a patched Inisght 6.8-1 release which should fix all outstanding issues with X11. 
[http://sourceware.org/insight/](http://sourceware.org/insight/)

The last insight package for Ubuntu (Karmic) is version 6.7.1. Realistically, it means that you'll have to compile the latest insight manually to have a fair chance of getting it to install (and work). Which will likely be no fun.

---

### Post by primo-itty on 2010-08-02
Hello, I me the same thing is happening, I did everything that was asked and the same problem, then downloaded the program from the site of insight but can not install, I do ./configure and when I do ```
make him the error: 
make [2]: ** [linux-Nat] Error 1
make [2]: Leaving directory `/ home/marcos/insight-6.8/gdb '
make [1]: ** [all-gdb] Error 2
make [1]: Leaving directory `/ home/marcos/insight-6.8 '
make: ** [all] Error 2 
```
in addition to several lines of error before

what do I do?

sorry, my english is terrible. I'm from Brazil.

---

