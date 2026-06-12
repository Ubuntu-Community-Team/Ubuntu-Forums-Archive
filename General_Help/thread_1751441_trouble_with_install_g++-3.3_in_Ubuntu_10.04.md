---
title: "trouble with install g++-3.3 in Ubuntu 10.04"
date: 2011-05-06
forum: General Help
---

### Post by lidengdeng on 2011-05-06
Hi guys:

g++4.4.3 has already been installed in Ubuntu 10.04. However, g++-3.3 is needed to compile a stupid source code (g++-4.4.3 does not work out).

I tried:
sudo apt-get install g++-3.3

but got:
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package g++3.3

Other g++ versions, including g++-4.1, g++-4.2, g++-4.3, and g++-4.4, are available. Why g++-3.3 is not on the list.....

Any tips to install g++-3.3?

Thanks...

---

### Post by chellrose on 2011-05-06
Try opening Synaptic and searching for g++, or
```
sudo apt-cache search g++
```

Likely the package name isn't exactly what you typed.

---

### Post by lidengdeng on 2011-05-06
> **Sissy13 said:**
> Try opening Synaptic and searching for g++, or
```
sudo apt-cache search g++
```

Likely the package name isn't exactly what you typed.

Thanks..

Searching g++ returned hundreds of results.

g++-3.3 does not on the result list when searching on synaptic package manager.....

---

### Post by lidengdeng on 2011-05-06
I downloaded gcc-3.3_3.3.6-10_i386.deb, g++-3.3_3.3.6-10_i386.deb, and gcc-3.3-base_3.3.6-10_i386.deb from [http://archive.ubuntu.com/ubuntu/pool/main/g/gcc-3.3/](http://archive.ubuntu.com/ubuntu/pool/main/g/gcc-3.3/)

Then installed gcc-3.3-base_3.3.6-10_i386.deb, Okay..

Installing gcc-3.3_3.3.6-10_i386.deb or g++-3.3_3.3.6-10_i386.deb get an error message saying Error: Dependency is not satisfiable: gcc-3.3 (= 1:3.3.6-10)

Does Ubuntu 10.04 no longer support g++-3.3 any more??

---

### Post by lidengdeng on 2011-05-06
Cool... It is resolved..

Thanks to [http://www.blitzbasic.com/Community/posts.php?topic=81247](http://www.blitzbasic.com/Community/posts.php?topic=81247)

---

### Post by chellrose on 2011-05-07
Cool, glad you were able to get it working.

---

