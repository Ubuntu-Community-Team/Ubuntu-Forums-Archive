---
title: "Issue migrating C program from Solaris to Linux."
date: 2009-09-11
forum: General Help
---

### Post by kuldippa on 2009-09-11
I have a C code on solaris ccompiled with gcc 3.2.1 version. Compliation command line is 
/usr/bin/gcc -g -I$SYBASE/OCS-12_5/include -L$SYBASE/OCS-12_5/lib -R$SYBASE/OCS-12_5/lib repdata.c generic.c -lct -lcs -lcomn -ltcl -lintl -lnsl -ldl -lm -o rpd
 
I compiled this code on Redhat Linux with gcc verison 4.1.2 using the command line 
 
/usr/bin/gcc -g -I$SYBASE/$SYBASE_OCS/include -L$SYBASE/OCS-15_0/lib repdata.c generic.c -lsybct64 -lsybcs64 -lsybcomn64 -lsybtcl64 -lsybintl64 -lnsl -ldl -lm -o repdata
 
The version of sybase has changed from 12.5 to 15.0
 
There are few issues i am facing,
 
1) On linux i am getting error "gcc: unrecognized option '-R/sybase/OCS-15_0/lib'". Is the -R option not available in gcc 4.1.2? If yes, how to I reference external libraries.
 
2) If i remove the -R option, my code compiles, but when i run teh code I get the error from the sybase like below.
 
Server message:
Message number: 8589940293, Severity 7022344801645520231, State 7953753053885104138, Line 322497432
Procedure ''
Message String: base context to 'cloning'.
 
I have no experience with C programming. I am just trying to migrate one C program from solaris to Linux. Any help would be appreciated.

---

### Post by flugh on 2009-09-11
I'm way out on a limb here, back up your web browser before reading this!

I googled this up regarding -R (I hadn't used it before in my limited coding experience). There's a work-around using an option file in same dir as 'cc1' mentioned, but also pretty strong sentiments against doing this.

[http://gcc.gnu.org/faq.html#rpath](http://gcc.gnu.org/faq.html#rpath)

I know the -L can be used to pass non-system-specified library paths to gcc (like in a sub-dir of your personal code project or something). The system's 'standard' path is defined in /etc/ld.so.conf I -think- (very similar name if not).

There were a few notes that may be of interest to you at:
[http://www.eyrie.org/~eagle/notes/rpath.html](http://www.eyrie.org/~eagle/notes/rpath.html)

Hope something helps. Good luck.

---

