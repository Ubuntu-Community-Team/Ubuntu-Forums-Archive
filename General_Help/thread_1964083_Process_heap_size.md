---
title: "Process heap size"
date: 2012-04-23
forum: General Help
---

### Post by dahakam on 2012-04-23
Hi everyone, 

i am newbie at ubuntu and kernel programming.
What i want to ask is when i taking map output with the help of "cat map" function i want to calculate exact space of heap

```
00400000-004df000 r-xp 00000000 08:01 917510                             /bin/bash
006de000-006df000 r--p 000de000 08:01 917510                             /bin/bash
006df000-006e8000 rw-p 000df000 08:01 917510                             /bin/bash
006e8000-006ee000 rw-p 00000000 00:00 0 
018aa000-01aee000 rw-p 00000000 00:00 0                                  [heap]
7f3270eac000-7f3270eb8000 r-xp 00000000 08:01 397444                     /lib/x86_64-linux-gnu/libnss_files-2.13.so
7f3270eb8000-7f32710b7000 ---p 0000c000 08:01 397444                     /lib/x86_64-linux-gnu/libnss_files-2.13.so
7f32710b7000-7f32710b8000 r--p 0000b000 08:01 397444                     /lib/x86_64-linux-gnu/libnss_files-2.13.so
7f32710b8000-7f32710b9000 rw-p 0000c000 08:01 397444                     /lib/x86_64-linux-gnu/libnss_files-2.13.so
7f32710b9000-7f32710c3000 r-xp 00000000 08:01 397448                     /lib/x86_64-linux-gnu/libnss_nis-2.13.so
7f32710c3000-7f32712c3000 ---p 0000a000 08:01 397448                     /lib/x86_64-linux-gnu/libnss_nis-2.13.so
7f32712c3000-7f32712c4000 r--p 0000a000 08:01 397448                     /lib/x86_64-linux-gnu/libnss_nis-2.13.so
7f32712c4000-7f32712c5000 rw-p 0000b000 08:01 397448                     /lib/x86_64-linux-gnu/libnss_nis-2.13.so
7f32712c5000-7f32712dc000 r-xp 00000000 08:01 397438                     /lib/x86_64-linux-gnu/libnsl-2.13.so
7f32712dc000-7f32714db000 ---p 00017000 08:01 397438                     /lib/x86_64-linux-gnu/libnsl-2.13.so
7f32714db000-7f32714dc000 r--p 00016000 08:01 397438                     /lib/x86_64-linux-gnu/libnsl-2.13.so
7f32714dc000-7f32714dd000 rw-p 00017000 08:01 397438                     /lib/x86_64-linux-gnu/libnsl-2.13.so
7f32714dd000-7f32714df000 rw-p 00000000 00:00 0 

```

it is the sample of my output.
According to ubuntu guide "018aa000-01aee000 " 
it is the address of heap in hex format but i dont understand its exact space or interval?

---

### Post by dahakam on 2012-04-24
As a help for people who can face same problem

"018aa000" -> means starting address space

"01aee000" -> means ending address space

as a note addresses are in hexadecimal format

---

