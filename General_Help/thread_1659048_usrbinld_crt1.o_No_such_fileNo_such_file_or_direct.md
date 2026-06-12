---
title: "/usr/bin/ld: crt1.o: No such file:No such file or directory"
date: 2011-01-03
forum: General Help
---

### Post by angelos.angelopoulos on 2011-01-03
My Best Wishes for a Happy , Healthy and Productive New Year to all.
I have Installed UBUNTU 10.04 TLS and Iam working with that for some time. Recently I discovered the following Problem. I use fortran for my work and I use both G77 and GFORTRAN  Few days ago when I try to compile a program, with any of the compilers but also for gcc, I get the following message:
[B]gfortran testx.f95 -o testx.e
/usr/bin/ld: crt1.o: No such file: No such file or directory
collect2: ld returned 1 exit status[/B]
Searching for help I found that the same problem happened to other colleagues also but they solved the problem by installing the libc6-dev. However this does not work for me. I reinstalled G77, Gfortran and gcc and I checked that all the necessary files exist in places I expect to be.
Is there any other advice except the complete and clean re-installation of the operating system ?
Thanks in advance for any answer which may help me.
Angelos

---

### Post by shademere on 2012-01-09
Hello, I'm having the same problem, and yes, Happy New Year to you as well. I'm also using fortran, and when I try installed gcc-4.7 and tried to compile using gfortran, it too gave the same error. Did you solve your problem?

---

