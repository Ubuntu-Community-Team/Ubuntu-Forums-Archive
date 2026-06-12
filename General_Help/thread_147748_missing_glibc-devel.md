---
title: "missing glibc-devel?"
date: 2006-03-20
forum: General Help
---

### Post by LordMerlin on 2006-03-20
Hello all  :)  

I'm trying to install ROR on a newly installed ubuntu 5.10 machine, but  have very little luck. 

Apparently, I need glibc-devel in order to use gcc, but trying to  install it only gives me this message: 
root@Gimbli:/usr/local/src/ruby-1.8.3# apt-get install glibc-devel 
Reading package lists... Done 
Building dependency tree... Done 
E: Couldn't find package glibc-devel 

I did an apt-get update, but that didn't fix it. What am I missing?

---

### Post by Sutekh on 2006-03-20
If you want gcc install it using apt-get,  it will take care of the dependant packages.
```
sudo apt-get install gcc
```


The reason why you can't find glibc-devel is because it doesn't exist.  gcc depends on **libc6-dev**.  Check it out

[Ubuntu Packages - gcc](http://packages.ubuntu.com/breezy/devel/gcc)


_

---

### Post by LordMerlin on 2006-03-21
Awesome, thanx :)

Now I can finally install ruby on rails !!!!!

---

