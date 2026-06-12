---
title: "man pages for these?"
date: 2009-09-28
forum: General Help
---

### Post by abhilashm86 on 2009-09-28
when i use fedora in my college, it shows man pages for fwrite, malloc, fork and others, i don't find them in ubuntu? i tried installing, but errors, how to get them?
```
abhilash@abhi:~$ sudo apt-get install fwrite
[sudo] password for abhilash: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package fwrite
abhilash@abhi:~$ man malloc
No manual entry for malloc
abhilash@abhi:~$ man fork
No manual entry for fork
abhilash@abhi:~$ sudo apt-get install man fwrite
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Note, selecting man-db instead of man
man-db is already the newest version.
E: Couldn't find package fwrite
abhilash@abhi:~$ 

```
well how to get these man pages, they are nice referneces while coding........

---

### Post by lloyd_b on 2009-09-28
```
sudo apt-get install manpages-dev
``` will get you the man pages for the man(2) (system calls) and man(3) (standard library functions).

I have never understood why this package isn't part of "build-essential"...

Lloyd B.

---

### Post by badger_fruit on 2009-09-28
[http://www.manpagez.com/](http://www.manpagez.com/)

---

### Post by abhilashm86 on 2009-09-28
> **lloyd_b said:**
> ```
sudo apt-get install manpages-dev
``` will get you the man pages for the man(2) (system calls) and man(3) (standard library functions).

I have never understood why this package isn't part of "build-essential"...

Lloyd B.

thanks for info:) did it.......
yes even i was amazed by dpkg behaviour!! actually when we type something new software/tool, terminal will invoke saying how to install........
Lets hope in future that ubuntu will correct all these small problems

---

