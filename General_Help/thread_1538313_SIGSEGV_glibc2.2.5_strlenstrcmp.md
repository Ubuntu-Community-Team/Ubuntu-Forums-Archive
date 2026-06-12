---
title: "SIGSEGV glibc2.2.5 strlen/strcmp"
date: 2010-07-24
forum: General Help
---

### Post by rgrover on 2010-07-24
I'm running 10.04 on a 64bit machine. Many of my programs have started failing with a stack trace which resembles:

Program received signal SIGSEGV, Segmentation fault.
0x0000000000638660 in strlen@@GLIBC_2.2.5 ()
(gdb) where
#0  0x0000000000638660 in strlen@@GLIBC_2.2.5 ()
#1  0x0000000000413db4 in makepath (dir=0x7fffffffee3f "/home/rgrover", 
    file=0x42c807 ".globalrc", suffix=0x0) at makepath.c:64
#2  0x000000000040eb64 in configpath () at conf.c:212
#3  openconf () at conf.c:248
#4  0x0000000000403f51 in main (argc=0, argv=0x7fffffffe230) at gtags.c:408


I have a fairly up-to-date system.

I have found related posts in other forums indicating that either binutils or libc6* is out of date. I have tried updating these, but no luck.


$ apt-cache policy binutils
binutils:
  Installed: 2.20.1-3ubuntu6
  Candidate: 2.20.1-3ubuntu6
  Version table:
 *** 2.20.1-3ubuntu6 0
        500 [http://tw.archive.ubuntu.com/ubuntu/](http://tw.archive.ubuntu.com/ubuntu/) lucid-updates/main Packages
        100 /var/lib/dpkg/status
     2.20.1-3ubuntu5 0
        500 [http://tw.archive.ubuntu.com/ubuntu/](http://tw.archive.ubuntu.com/ubuntu/) lucid/main Packages


$ apt-cache policy libc6
libc6:
  Installed: 2.11.1-0ubuntu7.2
  Candidate: 2.11.1-0ubuntu7.2
  Version table:
 *** 2.11.1-0ubuntu7.2 0
        500 [http://tw.archive.ubuntu.com/ubuntu/](http://tw.archive.ubuntu.com/ubuntu/) lucid-updates/main Packages
        100 /var/lib/dpkg/status
     2.11.1-0ubuntu7.1 0
        500 [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) lucid-security/main Packages
     2.11.1-0ubuntu7 0
        500 [http://tw.archive.ubuntu.com/ubuntu/](http://tw.archive.ubuntu.com/ubuntu/) lucid/main Packages


Can anyone please help?
Thanks.

---

