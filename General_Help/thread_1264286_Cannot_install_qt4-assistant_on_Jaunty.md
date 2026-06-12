---
title: "Cannot install qt4-assistant on Jaunty"
date: 2009-09-12
forum: General Help
---

### Post by prasadbrg on 2009-09-12
Hello everyone,
  I need to install the qt4-assistant package on Jaunty 9.04 (32 bit). I've installed the qt3-assistant from the repos, and it works fine. Here's the problem:
```
sudo apt-get install qt4-assistant
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package qt4-assistant is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package qt4-assistant has no installation candidate
```
Incidentally, the package libqt4-assistant is installed. When I run 'assistant', the version that is shown is 3.3.8b.
  I would appreciate any help/pointers in this regard.
Thanks in advance!
Cheers,

Guru

---

### Post by prasadbrg on 2009-09-12
I should have done a bit more homework before posting the question. [This thread]("http://ubuntuforums.org/showthread.php?t=680751") already contained the solution to my problem. 
Anyways, I hope this is useful to someone...!
Cheers,

Guru

---

