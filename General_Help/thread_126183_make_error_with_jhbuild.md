---
title: "make error with jhbuild"
date: 2006-02-05
forum: General Help
---

### Post by lungdart on 2006-02-05
Hey, i downloaded the latest jhbuild from CVS and i try to compile it.

Theres no configure file, and the directions just say to run 'make install' and when i do i get this error

```

shawn@Lung-Zilla:~/cvs/gnome2/jhbuild$ make install
gcc -Wall -O2 -o install-check install-check.c
install-check.c:19:19: error: stdio.h: No such file or directory
install-check.c:20:20: error: stdlib.h: No such file or directory
install-check.c:21:20: error: string.h: No such file or directory
install-check.c:22:20: error: unistd.h: No such file or directory
install-check.c:23:19: error: errno.h: No such file or directory
install-check.c:24:23: error: sys/types.h: No such file or directory
install-check.c:25:22: error: sys/stat.h: No such file or directory
install-check.c:26:22: error: sys/wait.h: No such file or directory
install-check.c: In function ‘compare’:
install-check.c:32: error: storage size of ‘b1’ isn’t known
install-check.c:32: error: storage size of ‘b2’ isn’t known
install-check.c:34: error: ‘pid_t’ undeclared (first use in this function)
install-check.c:34: error: (Each undeclared identifier is reported only once
install-check.c:34: error: for each function it appears in.)
install-check.c:34: error: syntax error before ‘pid’
install-check.c:36: warning: implicit declaration of function ‘stat’
install-check.c:42: error: ‘pid’ undeclared (first use in this function)
install-check.c:42: warning: implicit declaration of function ‘fork’
install-check.c:45: warning: implicit declaration of function ‘execlp’
install-check.c:45: warning: incompatible implicit declaration of built-in function ‘execlp’
install-check.c:45: error: ‘NULL’ undeclared (first use in this function)
install-check.c:45: warning: missing sentinel in function call
install-check.c:50: error: ‘rpid’ undeclared (first use in this function)
install-check.c:50: warning: implicit declaration of function ‘waitpid’
install-check.c:51: error: ‘errno’ undeclared (first use in this function)
install-check.c:51: error: ‘EINTR’ undeclared (first use in this function)
install-check.c:56: warning: implicit declaration of function ‘WIFEXITED’
install-check.c:56: warning: implicit declaration of function ‘WEXITSTATUS’
install-check.c:57: warning: implicit declaration of function ‘exit’
install-check.c:57: warning: incompatible implicit declaration of built-in function ‘exit’
install-check.c:32: warning: unused variable ‘b2’
install-check.c:32: warning: unused variable ‘b1’
install-check.c: In function ‘main’:
install-check.c:64: error: storage size of ‘buf’ isn’t known
install-check.c:71: warning: implicit declaration of function ‘strrchr’
install-check.c:71: warning: incompatible implicit declaration of built-in function ‘strrchr’
install-check.c:72: error: ‘NULL’ undeclared (first use in this function)
install-check.c:74: warning: implicit declaration of function ‘strlen’
install-check.c:74: warning: incompatible implicit declaration of built-in function ‘strlen’
install-check.c:79: warning: implicit declaration of function ‘strcmp’
install-check.c:89: warning: implicit declaration of function ‘S_ISDIR’
install-check.c:109: warning: implicit declaration of function ‘malloc’
install-check.c:109: warning: incompatible implicit declaration of built-in function ‘malloc’
install-check.c:118: warning: implicit declaration of function ‘execv’
install-check.c:64: warning: unused variable ‘buf’
make: *** [install-check] Error 1

```

Looks like header files are missing? but i cant seem to find any on apt-get, and i have gcc and make installed. any ideas? I'm trying to get luminocity working for gnome so i can try some of its features out.

thanks in advance

P.S.: the directions im using to get jhbuild and install luminocity are [http://www.jamesh.id.au/software/jhbuild/](http://www.jamesh.id.au/software/jhbuild/) and [http://live.gnome.org/Luminocity#head-d8ce897db9271b9f1403c68d164f858f6ada8597](http://live.gnome.org/Luminocity#head-d8ce897db9271b9f1403c68d164f858f6ada8597) respectivly

---

### Post by RAOF on 2006-02-05
Do you have the "build-essential" package installed?  That package pulls in everything you need to compile (fairly simple) programs.

---

