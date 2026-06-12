---
title: "Can't build kst-1.9.1"
date: 2010-07-30
forum: General Help
---

### Post by wkulecz on 2010-07-30
Actually it appears to build just fine, but segfaults when run it :(

I'm following the recipe from here after downloading and extracting the tarball:
[http://kst.kde.org/download.html#stable](http://kst.kde.org/download.html#stable)

Compiling kst using automake:
```
 
./configure --prefix=/usr
make
sudo make install 

```

Everything appears to work but running the application fails with sigsegv :(

Actually the --prefix=/usr causes the apt-get installed kst to be overwritten, but I tried --prefix=/home/wally first and then did make clean with the "documented" command after it created code that crashed.  Uninstalling and re-installing kst in synaptic got my 1.5.1 kst back, but its got some issues I hope have been fixed.

I need to use Ubuntu 8.04 for this right now, but 10.04 has kst 1.7.1 which still has the issue so I'd need to build it there eventually too :(

In case you've never heard of Kst, its graphing program that when reading stdin can be used as a real-time strip-chart display.  The issues I have with the repo versions are --geometry option doesn't change the window start up size and the -F option (to start up with a *.kst file for nice labels and layout and use stdin for real-time data).

---

### Post by wkulecz on 2010-08-03
Bump!

I've never ran into a "stable" source tarball that appears to compile OK and then crashes when run :(

I've given up on plenty that seemed to throw way more ./configure errors or compliation errors than I'd have time to deal with, but this seemed to go smoothly until I actually try to run it.

---

