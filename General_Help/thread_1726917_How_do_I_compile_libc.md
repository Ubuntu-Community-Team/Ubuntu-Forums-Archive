---
title: "How do I compile libc?"
date: 2011-04-11
forum: General Help
---

### Post by Richard Wordingham on 2011-04-11
I can't work out how to compile libc.  I've downloaded what appears to be the source from package eglibc-source Version 2.11.1-0ubuntu7.8, unpacked the source from /usr/src/glibc/eglibc-2.11.1.tar.xz, created a sister directory to the directory eglibc-2.11.1, and from the directory issued the commands

../eglibc-2.11.1/configure --prefix /home/richard/locale_bug/aswas_data --exec-prefix /home/richard/locale_bug/aswas_exe
make

I rapidly had problems with inline expansions, which I seemingly cured by commenting out a few lines in misc/syslog.c, nptl/sysdeps/pthread/pt-longjmp.c and string/bits/string3.h, and changed void* to char* in headers in debug/readlink_chk.c and debug/readlinkat_chk.c to accord with the version of unistd.h they were being compiled with.  However, linking then fails in directory elf because of an undefined hidden symbol __stack_chk_fail_local allegedly referenced in rtld.c.  I'm not a GNU C programmer, so I don't know what next to try.

I'm running Lucid Lynx 10.04, gcc version4.4.3-4ubuntu5,  as version 2.20.1-system.20100303 and  uname -a yields
Linux JRWUBU2 2.6.32-30-generic #59-Ubuntu SMP Tue Mar 1 21:30:21 UTC 2011 i686 GNU/Linux

The reason I am trying to compile libc is that in the locale en_GB.utf8 characters from the scripts of Thailand compare as equal, so when I used sort -u to remove duplicate entries from some Tai Tham data, 478 unique lines were suddenly reduced to 14!  The immediate work around was to use the C locale, which did a nice clean binary comparison.  The cause of my sorting problem is that the en_GB collation data contains no entries for scripts Tai Tham (or indeed, Thai), and so their characters are compared equal.  (Major Indian scripts are supported in the en_GB locale, though there are probably problems with new characters.)  Now ISO/IEC 14651:2007 only suggests that unsupported characters should compare unequal to one another, so I can't call this unfortunate feature a bug.  To call for this feature to be removed, I feel I ought to at least try a solution out first.

---

### Post by Richard Wordingham on 2011-08-27
I've also tried downloading using apt-get source glibc and then unpacking using dpkg-source.  Using pbuilder compiled, linked, ran and deleted!  The deletion happened because of a test failure.  However, looking though the package's debian/rules gave me a hint to the solution.

The solution is to have environment variable CFLAGS set to [FONT=Courier New]-O2 -fno-stack-protector -U_FORTIFY_SOURCE[/FONT] when running [FONT=Courier New]configure[/FONT] as part of the conventional build process.

---

