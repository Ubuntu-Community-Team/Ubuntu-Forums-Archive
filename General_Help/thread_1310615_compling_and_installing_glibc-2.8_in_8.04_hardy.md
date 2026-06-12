---
title: "compling and installing glibc-2.8 in 8.04 hardy"
date: 2009-11-01
forum: General Help
---

### Post by Vigh on 2009-11-01
compling and installing glibc-2.8 in 8.04 hardy

Hi im trying to install and compile the GNU C Library, I thought it would be a simply matter of entering the directory typing in terminal-
sudo ./configure
sudo make
sudo make install

when I go to configure I get the error message

error: you must configure in a separate build directory

I know its probably something really simple. How do I fix this issue.

---

### Post by Vigh on 2009-11-02
managed to configure it, but I am now getting install error 2 when I type make install in the bash system, and in normal terminal


anthony@anthony-linux:~/Desktop/glibc-2.8/glibc-build$ make install
LANGUAGE=C LC_ALL=C; export LANGUAGE LC_ALL; \
	make -r PARALLELMFLAGS="" CVSOPTS="" -C /home/anthony/Desktop/glibc-2.8 objdir=`pwd` install
make[1]: Entering directory `/home/anthony/Desktop/glibc-2.8'
mawk -f scripts/gen-sorted.awk \
	       -v subdirs='csu assert ctype locale intl catgets math setjmp signal stdlib stdio-common libio malloc string wcsmbs time dirent grp pwd posix io termios resource misc socket sysvipc gmon gnulib iconv iconvdata wctype manual shadow po argp crypt nss localedata timezone rt conform debug  dlfcn elf' \
	       -v srcpfx='' \
	       nptl/sysdeps/pthread/Subdirs sysdeps/unix/inet/Subdirs sysdeps/unix/Subdirs assert/Depend intl/Depend catgets/Depend stdlib/Depend stdio-common/Depend libio/Depend malloc/Depend string/Depend wcsmbs/Depend time/Depend posix/Depend iconvdata/Depend nss/Depend localedata/Depend rt/Depend debug/Depend > /home/anthony/Desktop/glibc-2.8/glibc-build/sysd-sorted-tmp
mawk: scripts/gen-sorted.awk: line 19: regular expression compile failed (bad class -- [], [^] or [)
/[^
mawk: scripts/gen-sorted.awk: line 19: syntax error at or near ]
mawk: scripts/gen-sorted.awk: line 19: runaway regular expression /, "", subd ...
make[1]: *** No rule to make target `/home/anthony/Desktop/glibc-2.8/glibc-build/Versions.all', needed by `/home/anthony/Desktop/glibc-2.8/glibc-build/abi-versions.h'.  Stop.
make[1]: Leaving directory `/home/anthony/Desktop/glibc-2.8'
make: *** [install] Error 2
anthony@anthony-linux:~/Desktop/glibc-2.8/glibc-build$ 
anthony@anthony-linux:~/Desktop/glibc-2.8/glibc-build$

---

