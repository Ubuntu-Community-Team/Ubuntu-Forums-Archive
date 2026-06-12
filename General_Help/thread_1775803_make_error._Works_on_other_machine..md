---
title: "make error. Works on other machine."
date: 2011-06-05
forum: General Help
---

### Post by PaulusT on 2011-06-05
Edit: SOLVED

The solution is not really useful and I still have no idea how to debug problems of this nature.

In my case, I had not added something to my path before executing the configure script of llvm. I later added the directory to my path. Configuration files from llvm were included from the makefiles of the modified version of uclibc.

---

I am trying to compile a modified version of uclibc with llvm 2.6. This may sound tricky but the modified version compiles out of the box and I have achieved this already on my laptop.

For simplicity, I used Ubuntu 10.10 x64, which is what the developers (of this modified version) use. I installed the required packages first and everything worked perfectly.

I am now trying again on a different machine with Ubuntu 10.10 x64 inside VirtualBox. I cannot get it to work, so I am thinking that I must have downloaded some extra packages or something, as the files used are identical.

I am mainly hoping for the following:
- the make error can be recognised from some other similar situation and so you can provide me with some clues as to what is wrong, or
- you can provide me with some steps to help debug the problem, as I am amazed at how I have no idea what is actually happening behinds the scenes. (I think the fact that there are shell scripts involved makes this more difficult.)

Here is what happens:

```

paul@vzxc:~/Downloads/uclibc$ ./configure --with-llvm=/home/paul/Downloads/llvm-2.6
Using llvm... done


paul@vzxc:~/Downloads/uclibc$ make
/bin/sh: Illegal option --
make: --emit-llvm: Command not found
make: --emit-llvm: Command not found
/bin/sh: Illegal option --
make[1]: --emit-llvm: Command not found
make[1]: --emit-llvm: Command not found
extra/scripts/gen_bits_syscall_h.sh: 46: --emit-llvm: not found
extra/scripts/gen_bits_syscall_h.sh: 46: --emit-llvm: not found
  CC libcrypt/crypt.os
/bin/sh: --emit-llvm: not found
make: *** [libcrypt/crypt.os] Error 127


paul@vzxc:~/Downloads/uclibc$ remake
/bin/sh: Illegal option --
remake: --emit-llvm: Command not found
remake: --emit-llvm: Command not found
/bin/sh: Illegal option --
remake[1]: --emit-llvm: Command not found
remake[1]: --emit-llvm: Command not found
extra/scripts/gen_bits_syscall_h.sh: 46: --emit-llvm: not found
extra/scripts/gen_bits_syscall_h.sh: 46: --emit-llvm: not found
  CC libcrypt/crypt.os
/bin/sh: --emit-llvm: not found
Makerules:35: *** [libcrypt/crypt.os] Error 127

#0  libcrypt/crypt.os at /home/paul/Downloads/uclibc/Makerules:35
#1  lib/libcrypt.a at /home/paul/Downloads/uclibc/libcrypt/Makefile.in:55
#2  libs at /home/paul/Downloads/uclibc/Makerules:17
#3  all at /home/paul/Downloads/uclibc/Makefile.in:20

paul@vzxc:~/Downloads/uclibc$ remake -d | head --lines=30
GNU Make + Debugger 3.81+dbg-0.2
Copyright (C) 2002, 2003, 2004, 2006, 2008 Free Software Foundation, Inc.
This is free software; see the source for copying conditions.
There is NO warranty; not even for MERCHANTABILITY or FITNESS FOR A
PARTICULAR PURPOSE.

This program built for x86_64-pc-linux-gnu
Reading makefiles...
Reading makefile `Makefile'...
/home/paul/Downloads/uclibc/Makefile:12
	Reading makefile `Makefile.in' (search path) (no ~ expansion)...
/home/paul/Downloads/uclibc/Makefile.in:15
	Reading makefile `Rules.mak' (search path) (no ~ expansion)...
/home/paul/Downloads/uclibc/Rules.mak:37
	Reading makefile `/home/paul/Downloads/llvm-2.6//Makefile.config' (search path) (no ~ expansion)...
/home/paul/Downloads/uclibc/Rules.mak:70
	Reading makefile `.config' (search path) (don't care) (no ~ expansion)...
/bin/sh: Illegal option --
remake: --emit-llvm: Command not found
remake: --emit-llvm: Command not found
/home/paul/Downloads/uclibc/Makefile.in:23
	Reading makefile `.config.cmd' (search path) (don't care) (no ~ expansion)...
/home/paul/Downloads/uclibc/Makefile.in:25
	Reading makefile `ldso/Makefile.in' (search path) (no ~ expansion)...
/home/paul/Downloads/uclibc/ldso/Makefile.in:8
	Reading makefile `ldso/ldso/Makefile.in' (search path) (no ~ expansion)...
/home/paul/Downloads/uclibc/ldso/Makefile.in:9
	Reading makefile `ldso/libdl/Makefile.in' (search path) (no ~ expansion)...
/home/paul/Downloads/uclibc/Makefile.in:26
	Reading makefile `libcrypt/Makefile.in' (search path) (no ~ expansion)...
/home/paul/Downloads/uclibc/Makefile.in:27
	Reading makefile `libintl/Makefile.in' (search path) (no ~ expansion)...
/home/paul/Downloads/uclibc/Makefile.in:28


```

Thanks,
Paul

---

### Post by SaneWarning on 2011-06-05
ok, not really sure what your doing but i notice some stuff to do with /bin/sh that I've seen some people have problems with, as /bin/sh it is a symlink to /bin/dash and some scripts expect /bin/sh to be a symlink to /bin/bash so you could try changing /bin/sh to /bin/bash in your script. To see if that helps your problem.

---

### Post by PaulusT on 2011-06-05
Good idea!... but unfortunately, I have tried that. I have also considered that the files might have Windows line endings (but I believe this is not the case).

--emit-llvm is supposed to be an argument to llvm-gcc or a similar tool, not a command. I just wish I could see what was being executed. Modifying the scripts mentioned so that they echo certain vars or give verbose output does not seem to make any difference. Is the output from these scripts absorbed by make somehow?

Again, I have this working on another machine, so any suggestions of how to compare what is different may help. But I would also particularly like to know what is happening here!

---

### Post by gmargo on 2011-06-05
Since they're both 10.10 machines you should start by comparing a list of installed packages on each machine.  Diffing the lists might make something stand out.

You can use **dpkg** to get the list.  (I add the COLUMNS environment variable because dpkg stupidly pays attention to the terminal width, causing information loss.)
```

COLUMNS=200 dpkg -l > ~/pkgs

```Or use a less verbose listing:
```

dpkg --get-selections

```

---

### Post by PaulusT on 2011-06-05
Thank you that is a good idea! I've added the missing packages but still get the error. Also just confirmed that /bin/sh points to the same file on both machines.

I can't even do make clean without getting similar errors:

```

$ make clean
/bin/sh: Illegal option --
make: --emit-llvm: Command not found
make: --emit-llvm: Command not found
rm -f lib*/*.a ldso/*/*.a libpthread/*/*.a
rm -f include/fpu_control.h include/dl-osinfo.h include/hp-timing.h
make -C extra/locale locale_clean
/bin/sh: Illegal option --
......

```

I really wish I could debug what is happening here.




Edit: SOLVED

The solution is not really useful and I still have no idea how to debug problems of this nature.

In my case, I had not added something to my path before executing the configure script of llvm. I later added the directory to my path. Configuration files from llvm were included from the makefiles of the modified version of uclibc.

---

