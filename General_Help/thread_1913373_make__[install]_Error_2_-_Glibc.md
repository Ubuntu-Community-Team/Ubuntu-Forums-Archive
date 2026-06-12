---
title: "make: *** [install] Error 2 - Glibc"
date: 2012-01-22
forum: General Help
---

### Post by Ibraim on 2012-01-22
Hi people, i'm trying to install glibc, any version, but I can't because the following error:
I need glibc installed to install Babytrans translator. 

(Please, any problem with my post, alert me, i'm new here. Thanks)

I read another posts here, but didn't work.

```

ibraim@ibraim-H24Z:~/glibc/build-glibc$ make
make -r PARALLELMFLAGS="" CVSOPTS="" -C ./../glibc-2.14.1 objdir=`pwd` all
make[1]: Entering directory `/home/ibraim/glibc/glibc-2.14.1'
(echo 'sysd-rules-sysdirs := sysdeps/i386/elf nptl/sysdeps/unix/sysv/linux/i386/i686 sysdeps/unix/sysv/linux/i386/i686 nptl/sysdeps/unix/sysv/linux/i386 sysdeps/unix/sysv/linux/i386 nptl/sysdeps/unix/sysv/linux nptl/sysdeps/pthread sysdeps/pthread sysdeps/unix/sysv/linux sysdeps/gnu sysdeps/unix/common sysdeps/unix/mman sysdeps/unix/inet sysdeps/unix/sysv/i386 nptl/sysdeps/unix/sysv sysdeps/unix/sysv sysdeps/unix/i386 nptl/sysdeps/unix sysdeps/unix sysdeps/posix sysdeps/i386/i686/fpu sysdeps/i386/i686/multiarch nptl/sysdeps/i386/i686 sysdeps/i386/i686 sysdeps/i386/i486 nptl/sysdeps/i386/i486 sysdeps/i386/fpu nptl/sysdeps/i386 sysdeps/i386 sysdeps/wordsize-32 sysdeps/ieee754/ldbl-96 sysdeps/ieee754/dbl-64 sysdeps/ieee754/flt-32 sysdeps/ieee754 sysdeps/generic/elf sysdeps/generic';              \
     for dir in sysdeps/i386/elf nptl/sysdeps/unix/sysv/linux/i386/i686 sysdeps/unix/sysv/linux/i386/i686 nptl/sysdeps/unix/sysv/linux/i386 sysdeps/unix/sysv/linux/i386 nptl/sysdeps/unix/sysv/linux nptl/sysdeps/pthread sysdeps/pthread sysdeps/unix/sysv/linux sysdeps/gnu sysdeps/unix/common sysdeps/unix/mman sysdeps/unix/inet sysdeps/unix/sysv/i386 nptl/sysdeps/unix/sysv sysdeps/unix/sysv sysdeps/unix/i386 nptl/sysdeps/unix sysdeps/unix sysdeps/posix sysdeps/i386/i686/fpu sysdeps/i386/i686/multiarch nptl/sysdeps/i386/i686 sysdeps/i386/i686 sysdeps/i386/i486 nptl/sysdeps/i386/i486 sysdeps/i386/fpu nptl/sysdeps/i386 sysdeps/i386 sysdeps/wordsize-32 sysdeps/ieee754/ldbl-96 sysdeps/ieee754/dbl-64 sysdeps/ieee754/flt-32 sysdeps/ieee754 sysdeps/generic/elf sysdeps/generic; do                  \
       case "$dir" in                              \
       /*) ;;                                  \
       *) dir="\$(..)$dir" ;;                          \
       esac;                                  \
       asm='.S .s';                                  \
                                     \
       for o in .o .os .op .og .ob .oS; do                      \
         set % % rtld-% rtld-% rtld-% % m_% s_% ptw-% %;                  \
         while [ $# -ge 2 ]; do                          \
           t=$1; shift;                               \
           d=$1; shift;                              \
           v=${t%%%}; [ x"$v" = x ] || v="\$(${v}CPPFLAGS)";          \
           for s in $asm .c; do                          \
         echo "\$(objpfx)$t$o: $dir/$d$s \$(before-compile)";  \
         echo "    \$(compile-command$s) $v";                  \
           done;                                  \
         done;                                  \
       done;                                  \
       echo "\$(inst_includedir)/%.h: $dir/%.h \$(+force)";          \
       echo "    \$(do-install)";                       \
     done;                                      \
     echo 'sysd-rules-done = t') > /home/ibraim/glibc/build-glibc/sysd-rulesT
mv -f /home/ibraim/glibc/build-glibc/sysd-rulesT /home/ibraim/glibc/build-glibc/sysd-rules
for dir in /home/ibraim/glibc/build-glibc sysdeps/i386/elf nptl/sysdeps/unix/sysv/linux/i386/i686 sysdeps/unix/sysv/linux/i386/i686 nptl/sysdeps/unix/sysv/linux/i386 sysdeps/unix/sysv/linux/i386 nptl/sysdeps/unix/sysv/linux nptl/sysdeps/pthread sysdeps/pthread sysdeps/unix/sysv/linux sysdeps/gnu sysdeps/unix/common sysdeps/unix/mman sysdeps/unix/inet sysdeps/unix/sysv/i386 nptl/sysdeps/unix/sysv sysdeps/unix/sysv sysdeps/unix/i386 nptl/sysdeps/unix sysdeps/unix sysdeps/posix sysdeps/i386/i686/fpu sysdeps/i386/i686/multiarch nptl/sysdeps/i386/i686 sysdeps/i386/i686 sysdeps/i386/i486 nptl/sysdeps/i386/i486 sysdeps/i386/fpu nptl/sysdeps/i386 sysdeps/i386 sysdeps/wordsize-32 sysdeps/ieee754/ldbl-96 sysdeps/ieee754/dbl-64 sysdeps/ieee754/flt-32 sysdeps/ieee754 sysdeps/generic/elf sysdeps/generic  nptl; do \
      test -f $dir/syscalls.list && \
      { sysdirs='sysdeps/i386/elf nptl/sysdeps/unix/sysv/linux/i386/i686 sysdeps/unix/sysv/linux/i386/i686 nptl/sysdeps/unix/sysv/linux/i386 sysdeps/unix/sysv/linux/i386 nptl/sysdeps/unix/sysv/linux nptl/sysdeps/pthread sysdeps/pthread sysdeps/unix/sysv/linux sysdeps/gnu sysdeps/unix/common sysdeps/unix/mman sysdeps/unix/inet sysdeps/unix/sysv/i386 nptl/sysdeps/unix/sysv sysdeps/unix/sysv sysdeps/unix/i386 nptl/sysdeps/unix sysdeps/unix sysdeps/posix sysdeps/i386/i686/fpu sysdeps/i386/i686/multiarch nptl/sysdeps/i386/i686 sysdeps/i386/i686 sysdeps/i386/i486 nptl/sysdeps/i386/i486 sysdeps/i386/fpu nptl/sysdeps/i386 sysdeps/i386 sysdeps/wordsize-32 sysdeps/ieee754/ldbl-96 sysdeps/ieee754/dbl-64 sysdeps/ieee754/flt-32 sysdeps/ieee754 sysdeps/generic/elf sysdeps/generic' \
        asm_CPP='gcc -c  -Iinclude  -I/home/ibraim/glibc/build-glibc -Isysdeps/i386/elf -Inptl/sysdeps/unix/sysv/linux/i386/i686 -Isysdeps/unix/sysv/linux/i386/i686 -Inptl/sysdeps/unix/sysv/linux/i386 -Isysdeps/unix/sysv/linux/i386 -Inptl/sysdeps/unix/sysv/linux -Inptl/sysdeps/pthread -Isysdeps/pthread -Isysdeps/unix/sysv/linux -Isysdeps/gnu -Isysdeps/unix/common -Isysdeps/unix/mman -Isysdeps/unix/inet -Isysdeps/unix/sysv/i386 -Inptl/sysdeps/unix/sysv -Isysdeps/unix/sysv -Isysdeps/unix/i386 -Inptl/sysdeps/unix -Isysdeps/unix -Isysdeps/posix -Isysdeps/i386/i686/fpu -Isysdeps/i386/i686/multiarch -Inptl/sysdeps/i386/i686 -Isysdeps/i386/i686 -Isysdeps/i386/i486 -Inptl/sysdeps/i386/i486 -Isysdeps/i386/fpu -Inptl/sysdeps/i386 -Isysdeps/i386 -Isysdeps/wordsize-32 -Isysdeps/ieee754/ldbl-96 -Isysdeps/ieee754/dbl-64 -Isysdeps/ieee754/flt-32 -Isysdeps/ieee754 -Isysdeps/generic/elf -Isysdeps/generic -Inptl   -Ilibio -I.  -D_LIBC_REENTRANT -include include/libc-symbols.h       -DASSEMBLER  -DGAS_SYNTAX -g -Wa,--noexecstack   -E -x assembler-with-cpp' \
        /bin/sh sysdeps/unix/make-syscalls.sh $dir || exit 1; }; \
      test $dir = sysdeps/unix && break; \
    done > /home/ibraim/glibc/build-glibc/sysd-syscallsT
mv -f /home/ibraim/glibc/build-glibc/sysd-syscallsT /home/ibraim/glibc/build-glibc/sysd-syscalls
mawk -f scripts/gen-sorted.awk \
           -v subdirs='csu assert ctype locale intl catgets math setjmp signal stdlib stdio-common libio malloc string wcsmbs time dirent grp pwd posix io termios resource misc socket sysvipc gmon gnulib iconv iconvdata wctype manual shadow gshadow po argp crypt nss localedata timezone rt conform debug libidn dlfcn elf' \
           -v srcpfx='' \
           nptl/sysdeps/pthread/Subdirs sysdeps/unix/inet/Subdirs sysdeps/unix/Subdirs assert/Depend intl/Depend catgets/Depend stdlib/Depend stdio-common/Depend libio/Depend malloc/Depend string/Depend wcsmbs/Depend time/Depend posix/Depend iconvdata/Depend nss/Depend localedata/Depend rt/Depend debug/Depend > /home/ibraim/glibc/build-glibc/sysd-sorted-tmp
mawk: scripts/gen-sorted.awk: line 19: regular expression compile failed (bad class -- [], [^] or [)
/[^
mawk: scripts/gen-sorted.awk: line 19: syntax error at or near ]
mawk: scripts/gen-sorted.awk: line 19: runaway regular expression /, "", subd ...
make[1]: Leaving directory `/home/ibraim/glibc/glibc-2.14.1'
make[1]: Entering directory `/home/ibraim/glibc/glibc-2.14.1'
{ echo '#include "posix/bits/posix1_lim.h"';        \
      echo '#define _LIBC 1';                    \
      echo '#include "misc/sys/uio.h"'; } |            \
    gcc -E -dM -MD -MP -MF /home/ibraim/glibc/build-glibc/bits/stdio_lim.dT -MT '/home/ibraim/glibc/build-glibc/bits/stdio_lim.h /home/ibraim/glibc/build-glibc/bits/stdio_lim.d'     \
          -Iinclude  -I/home/ibraim/glibc/build-glibc -Isysdeps/i386/elf -Inptl/sysdeps/unix/sysv/linux/i386/i686 -Isysdeps/unix/sysv/linux/i386/i686 -Inptl/sysdeps/unix/sysv/linux/i386 -Isysdeps/unix/sysv/linux/i386 -Inptl/sysdeps/unix/sysv/linux -Inptl/sysdeps/pthread -Isysdeps/pthread -Isysdeps/unix/sysv/linux -Isysdeps/gnu -Isysdeps/unix/common -Isysdeps/unix/mman -Isysdeps/unix/inet -Isysdeps/unix/sysv/i386 -Inptl/sysdeps/unix/sysv -Isysdeps/unix/sysv -Isysdeps/unix/i386 -Inptl/sysdeps/unix -Isysdeps/unix -Isysdeps/posix -Isysdeps/i386/i686/fpu -Isysdeps/i386/i686/multiarch -Inptl/sysdeps/i386/i686 -Isysdeps/i386/i686 -Isysdeps/i386/i486 -Inptl/sysdeps/i386/i486 -Isysdeps/i386/fpu -Inptl/sysdeps/i386 -Isysdeps/i386 -Isysdeps/wordsize-32 -Isysdeps/ieee754/ldbl-96 -Isysdeps/ieee754/dbl-64 -Isysdeps/ieee754/flt-32 -Isysdeps/ieee754 -Isysdeps/generic/elf -Isysdeps/generic -Inptl   -Ilibio -I.  -xc - -o /home/ibraim/glibc/build-glibc/bits/stdio_lim.hT
sed -e 's@ /home/ibraim/glibc/build-glibc/@ $(common-objpfx)@g' -e 's@^/home/ibraim/glibc/build-glibc/@$(common-objpfx)@g' -e 's@  *\([^     \/$][^ \]*\)@ $(..)\1@g' -e 's@^\([^     \/$][^     \]*\)@$(..)\1@g'            \
        /home/ibraim/glibc/build-glibc/bits/stdio_lim.dT > /home/ibraim/glibc/build-glibc/bits/stdio_lim.dt
mv -f /home/ibraim/glibc/build-glibc/bits/stdio_lim.dt /home/ibraim/glibc/build-glibc/bits/stdio_lim.d
fopen_max=`sed -n 's/^#define OPEN_MAX //1p' /home/ibraim/glibc/build-glibc/bits/stdio_lim.hT`;     \
    filename_max=`sed -n 's/^#define PATH_MAX //1p' /home/ibraim/glibc/build-glibc/bits/stdio_lim.hT`;    \
    iov_max=`sed -n 's/^#define UIO_MAXIOV //p' /home/ibraim/glibc/build-glibc/bits/stdio_lim.hT`;    \
    fopen_max=${fopen_max:-16};                    \
    filename_max=${filename_max:-1024};                \
    if [ -z "$iov_max" ]; then                    \
      define_iov_max="# undef IOV_MAX";                \
    else                                \
      define_iov_max="# define IOV_MAX $iov_max";            \
    fi;                                \
    sed -e "s/@FOPEN_MAX@/$fopen_max/"                \
        -e "s/@FILENAME_MAX@/$filename_max/"            \
        -e "s/@L_tmpnam@/20/"                \
        -e "s/@TMP_MAX@/238328/"                \
        -e "s/@L_ctermid@/9/"                \
        -e "s/@L_cuserid@/9/"                \
        -e "s/@define_IOV_MAX@/$define_iov_max/"            \
        stdio-common/stdio_lim.h.in > /home/ibraim/glibc/build-glibc/bits/stdio_lim.h.new
/bin/sh scripts/move-if-change /home/ibraim/glibc/build-glibc/bits/stdio_lim.h.new /home/ibraim/glibc/build-glibc/bits/stdio_lim.h
rm -f /home/ibraim/glibc/build-glibc/bits/stdio_lim.hT /home/ibraim/glibc/build-glibc/bits/stdio_lim.dT /home/ibraim/glibc/build-glibc/bits/stdio_lim.dt
touch /home/ibraim/glibc/build-glibc/bits/stdio_lim.st
mawk -f scripts/gen-sorted.awk \
           -v subdirs='csu assert ctype locale intl catgets math setjmp signal stdlib stdio-common libio malloc string wcsmbs time dirent grp pwd posix io termios resource misc socket sysvipc gmon gnulib iconv iconvdata wctype manual shadow gshadow po argp crypt nss localedata timezone rt conform debug libidn dlfcn elf' \
           -v srcpfx='' \
           nptl/sysdeps/pthread/Subdirs sysdeps/unix/inet/Subdirs sysdeps/unix/Subdirs assert/Depend intl/Depend catgets/Depend stdlib/Depend stdio-common/Depend libio/Depend malloc/Depend string/Depend wcsmbs/Depend time/Depend posix/Depend iconvdata/Depend nss/Depend localedata/Depend rt/Depend debug/Depend > /home/ibraim/glibc/build-glibc/sysd-sorted-tmp
mawk: scripts/gen-sorted.awk: line 19: regular expression compile failed (bad class -- [], [^] or [)
/[^
mawk: scripts/gen-sorted.awk: line 19: syntax error at or near ]
mawk: scripts/gen-sorted.awk: line 19: runaway regular expression /, "", subd ...
make[1]: Leaving directory `/home/ibraim/glibc/glibc-2.14.1'
make[1]: Entering directory `/home/ibraim/glibc/glibc-2.14.1'
mawk -f scripts/gen-sorted.awk \
           -v subdirs='csu assert ctype locale intl catgets math setjmp signal stdlib stdio-common libio malloc string wcsmbs time dirent grp pwd posix io termios resource misc socket sysvipc gmon gnulib iconv iconvdata wctype manual shadow gshadow po argp crypt nss localedata timezone rt conform debug libidn dlfcn elf' \
           -v srcpfx='' \
           nptl/sysdeps/pthread/Subdirs sysdeps/unix/inet/Subdirs sysdeps/unix/Subdirs assert/Depend intl/Depend catgets/Depend stdlib/Depend stdio-common/Depend libio/Depend malloc/Depend string/Depend wcsmbs/Depend time/Depend posix/Depend iconvdata/Depend nss/Depend localedata/Depend rt/Depend debug/Depend > /home/ibraim/glibc/build-glibc/sysd-sorted-tmp
mawk: scripts/gen-sorted.awk: line 19: regular expression compile failed (bad class -- [], [^] or [)
/[^
mawk: scripts/gen-sorted.awk: line 19: syntax error at or near ]
mawk: scripts/gen-sorted.awk: line 19: runaway regular expression /, "", subd ...
rm -f /home/ibraim/glibc/build-glibc/stamp.o; > /home/ibraim/glibc/build-glibc/stamp.o
rm -f /home/ibraim/glibc/build-glibc/stamp.os; > /home/ibraim/glibc/build-glibc/stamp.os
rm -f /home/ibraim/glibc/build-glibc/stamp.oS; > /home/ibraim/glibc/build-glibc/stamp.oS
cd /home/ibraim/glibc/build-glibc && ar cruv libc.a `cat stamp.o`
cd /home/ibraim/glibc/build-glibc && ar cruv libc_pic.a `cat stamp.os`
cd /home/ibraim/glibc/build-glibc && ar cruv libc_nonshared.a `cat stamp.oS`
make[1]: *** No rule to make target `/home/ibraim/glibc/build-glibc/Versions.all', needed by `/home/ibraim/glibc/build-glibc/abi-versions.h'.  Stop.
make[1]: Leaving directory `/home/ibraim/glibc/glibc-2.14.1'
make: *** [all] Error 2

``````

make[1]: *** No rule to make target  `/home/ibraim/glibc/build-glibc/Versions.all', needed by  `/home/ibraim/glibc/build-glibc/abi-versions.h'.  Stop.
make[1]: Leaving directory `/home/ibraim/glibc/glibc-2.14.1'
make: *** [all] Error 2

```Can someone help me please?

Thanks a lot for any help! :confused:

---

