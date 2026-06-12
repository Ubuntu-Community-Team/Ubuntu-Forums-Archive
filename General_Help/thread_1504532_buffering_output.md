---
title: "buffering output"
date: 2010-06-08
forum: General Help
---

### Post by CyberWind on 2010-06-08
Hi,

When the program executed from a command line, instead of immediate output to file string by string, it accumulated in a buffer and then recorded into a file by a quite large block. It can be very inconvenient, if the program performs a lot of calculations but output just a few information. I have no this problem with Fedora and think that the problem is in system buffering. How it can be avoided? 
Program has been written on Fortran77 and can not be extremely modified.

---

### Post by iponeverything on 2010-06-08
maybe:

[http://www.tek-tips.com/viewthread.cfm?qid=1375255&page=4](http://www.tek-tips.com/viewthread.cfm?qid=1375255&page=4)

---

### Post by CyberWind on 2010-06-09
I solved it by setting variable GFORTRAN_UNBUFFERED_ALL to 1.

---

