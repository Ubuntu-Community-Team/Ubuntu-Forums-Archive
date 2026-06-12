---
title: "SIGBUS error /lib64/ld-linux-x86-64.so.2"
date: 2010-01-16
forum: General Help
---

### Post by jambli on 2010-01-16
Evening everyone,

I'm running into some issues when trying to run codeblocks on ubuntu 9.10 amd 64 bit.

When I attempt to run the program via terminal I get a Bus error.

```
desktop:~/Desktop$ codeblocks
Bus error
```Further digging using gdb displays the following results.

```
desktop:~/Desktop$ gdb codeblocks
(gdb) run
Starting program: /usr/bin/codeblocks 

Program received signal SIGBUS, Bus error.
0x00007ffff7df68f0 in ?? () from /lib64/ld-linux-x86-64.so.2
(gdb) bt
#0  0x00007ffff7df68f0 in ?? () from /lib64/ld-linux-x86-64.so.2
#1  0x00007ffff7de596d in ?? () from /lib64/ld-linux-x86-64.so.2
#2  0x00007ffff7de73a8 in ?? () from /lib64/ld-linux-x86-64.so.2
#3  0x00007ffff7deb46d in ?? () from /lib64/ld-linux-x86-64.so.2
#4  0x00007ffff7ded386 in ?? () from /lib64/ld-linux-x86-64.so.2
#5  0x00007ffff7debb64 in ?? () from /lib64/ld-linux-x86-64.so.2
#6  0x00007ffff7de27c7 in ?? () from /lib64/ld-linux-x86-64.so.2
#7  0x00007ffff7df43e7 in ?? () from /lib64/ld-linux-x86-64.so.2
#8  0x00007ffff7de038d in ?? () from /lib64/ld-linux-x86-64.so.2
#9  0x00007ffff7ddfaf8 in ?? () from /lib64/ld-linux-x86-64.so.2
#10 0x0000000000000001 in ?? ()
#11 0x00007fffffffe659 in ?? ()
#12 0x0000000000000000 in ?? ()

```From here I looked for what file this link actually pointed to.

```
desktop:~/Desktop$ readlink /lib64/ld-linux-x86-64.so.2
ld-2.10.1.so
```Nearest I can tell ld-2.10.1.so belongs to either libc6-amd64 or libc6 packages. I've tried reinstalling both in case it was a corrupt file to no avail.

At this point i'm completely lost at what to do. Also just let me know if you need any other information.

---

### Post by byStanderone on 2010-01-16
...sigbus error is a memory allocation error, usually happens when the system is short of available memory.

---

### Post by jambli on 2010-01-16
Pretty sure its not running out of memory system has 2 gigs and this happens when everything is closed.

And codeblocks runs fine on a system with maybe 512MBs of ram.

SIGBUS's also occur when memory is out of alignment, not just when it runs out of memory.

---

### Post by jambli on 2010-01-17
Solved. Truend out to be a problem in the libwx_gtk2u_core-2.8.so file. reinstallation seemed to fix it.

---

### Post by CyberRascal on 2010-01-18
Hi. It seems I have managed to run into the same problem, but on 32bit. Using kubuntu.

Running codeblocks in gdb yields a SIGBUS from /lib/ld-linux.so.2.
When you said reinstallation seemed to fix the problem, what kind of reinstallation do you mean.. What did you reinstall? I have tried reinstalling codeblocks..

---

### Post by jambli on 2010-08-02
Reinstall  /lib/ld-linux.so.2.

---

