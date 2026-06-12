---
title: "zlib cross compilation"
date: 2010-02-15
forum: General Help
---

### Post by shariefbe on 2010-02-15
i am tring to cross compile zlib-1.2.3.
In that also i am getting some error. It new one
when i use "AR=arm-none-linux-gnueabi-ar" option while configuration mean i am getting the below error
```

arm-none-linux-gnueabi-ar libz.a adler32.o compress.o crc32.o gzio.o uncompr.o deflate.o trees.o zutil.o inflate.o infback.o inftrees.o inffast.o 
arm-none-linux-gnueabi-ar: illegal option -- z
Usage: arm-none-linux-gnueabi-ar [emulation options] [-]{dmpqrstx}[abcfilNoPsSuvV] [member-name] [count] archive-file file...
       arm-none-linux-gnueabi-ar -M [<mri-script]
 commands:
  d            - delete file(s) from the archive
  m[ab]        - move file(s) in the archive
  p            - print file(s) found in the archive
  q[f]         - quick append file(s) to the archive
  r[ab][f][u]  - replace existing or insert new file(s) into the archive
  t            - display contents of archive
  x[o]         - extract file(s) from the archive
 command specific modifiers:
  [a]          - put file(s) after [member-name]
  [b]          - put file(s) before [member-name] (same as [i])
  [D]          - use zero for timestamps and uids/gids
  [N]          - use instance [count] of name
  [f]          - truncate inserted file names
  [P]          - use full path names when matching
  [o]          - preserve original dates
  [u]          - only replace files that are newer than current archive contents
 generic modifiers:
  [c]          - do not warn if the library had to be created
  [s]          - create an archive index (cf. ranlib)
  [S]          - do not build a symbol table
  [T]          - make a thin archive
  [v]          - be verbose
  [V]          - display the version number
  @<file>      - read options from <file>
 emulation options: 
  No emulation specific options
arm-none-linux-gnueabi-ar: supported targets: elf32-littlearm elf32-bigarm elf32-little elf32-big srec symbolsrec verilog tekhex binary ihex
make: *** [libz.a] Error 1

```
But when i remove that it is getting compiled. But when i give "make install" i am getting the below things 
```

sharief@sharief-desktop:/mnt/omap/sources/zlib-1.2.3$ make install
cp zlib.h zconf.h 
chmod 644 /zlib.h /zconf.h
chmod: cannot access `/zlib.h': No such file or directory
chmod: cannot access `/zconf.h': No such file or directory
make: *** [install] Error 1

```
eben if i change the permission as "777" i am getting the same error. I changed in Makefile also. still it is automatically changed to "644". Please help me

---

