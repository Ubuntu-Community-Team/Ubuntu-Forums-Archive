---
title: "Can't install systrace"
date: 2010-12-27
forum: General Help
---

### Post by daqron on 2010-12-27
Does anyone know how to install [systrace]("http://www.provos.org/index.php?/categories/2-Systrace") on 10.04 32-bit?

I tried installing the .deb linked from the systrace website and Package Installer tells me: "Error: Dependency is not satisfiable: libevent1 (>=1.1a)." I have libevent 1.4.11 installed.

I also tried compiling from source (which, interestingly, doesn't seem to have any problem finding libevent), but I get the following errors:

```
raindog@marmoset:~/Installers/systrace-1.6g$ make
make  all-recursive
make[1]: Entering directory `/home/raindog/Installers/systrace-1.6g'
Making all in .
make[2]: Entering directory `/home/raindog/Installers/systrace-1.6g'
gcc -DHAVE_CONFIG_H -I. -I. -I. -I/usr/local/include    -Wall  -c linux-ptrace-syscalls.c
In file included from linux-ptrace-syscalls.c:94:
linux_syscalls.c: In function &#8216;linux_syscall_name&#8217;:
linux_syscalls.c:719: warning: passing argument 1 of &#8216;generic_syscall_name&#8217; from incompatible pointer type
linux_syscalls.c:669: note: expected &#8216;const char **&#8217; but argument is of type &#8216;char **&#8217;
linux_syscalls.c: In function &#8216;linux_syscall_number&#8217;:
linux_syscalls.c:730: warning: assignment from incompatible pointer type
linux-ptrace-syscalls.c: In function &#8216;linux_rewritefork&#8217;:
linux-ptrace-syscalls.c:1149: error: &#8216;struct user_regs_struct&#8217; has no member named &#8216;cs&#8217;
linux-ptrace-syscalls.c: In function &#8216;linux_rewritewaitpid&#8217;:
linux-ptrace-syscalls.c:1297: error: &#8216;struct user_regs_struct&#8217; has no member named &#8216;cs&#8217;
linux-ptrace-syscalls.c: In function &#8216;linux_rewritewaitpid_return&#8217;:
linux-ptrace-syscalls.c:1341: error: &#8216;struct user_regs_struct&#8217; has no member named &#8216;cs&#8217;
linux-ptrace-syscalls.c: In function &#8216;linux_systemcall&#8217;:
linux-ptrace-syscalls.c:1564: error: &#8216;struct user_regs_struct&#8217; has no member named &#8216;cs&#8217;
linux-ptrace-syscalls.c:1564: error: &#8216;struct user_regs_struct&#8217; has no member named &#8216;cs&#8217;
linux-ptrace-syscalls.c:1570: error: &#8216;struct user_regs_struct&#8217; has no member named &#8216;cs&#8217;
make[2]: *** [linux-ptrace-syscalls.o] Error 1
make[2]: Leaving directory `/home/raindog/Installers/systrace-1.6g'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/home/raindog/Installers/systrace-1.6g'
make: *** [all] Error 2
```

Is this just bad code that won't run or am I doing something wrong? I should add, there's an "install-sh" file in the directory, but I've no idea what to do with that.

---

### Post by osmaneralp on 2011-01-05
FWIW, I'm having the same problem. Anyone know a solution? --Osman

---

