---
title: "Cannot build a &quot;hello world&quot; for a e500v2-Core target on Ubuntu 10.04"
date: 2012-10-08
forum: General Help
---

### Post by alfonsokame on 2012-10-08
[SIZE=3][FONT=Calibri]I ve built a simple hello world application by using this powerpc toolchain here ([http://downloads.yoctoproject.org/releases/yocto/yocto-1.2/toolchain/i686/](http://downloads.yoctoproject.org/releases/yocto/yocto-1.2/toolchain/i686/)). Im not able to execute it on the Freescale p1021-board (".\testapp"). It says "no such file or directory".[/FONT][/SIZE]
[SIZE=3][FONT=Calibri]the file has RW rights (chmod 777 testapp)and root is the owner.[/FONT][/SIZE]
[SIZE=3][FONT=Calibri]I tried "file testapp" and i get "ELF 32 bit executable PowerPC or cisco 4500, version 1 (SYSV), statically linked (uses shared libs), stripped".[/FONT][/SIZE]
[FONT=Calibri][SIZE=3]Im working on a Ubuntu virtual machine that run on Windows 7 64bit.[/SIZE][/FONT]
[FONT=Calibri][SIZE=3]When I do "uname -a", I get this: "Linux freescale-sdk 2.6.32-28-generic i686 GNU/Linux[/SIZE][/FONT]
[SIZE=3][FONT=Calibri]What am I missing here? can you help me please?[/FONT][/SIZE]
 
[SIZE=3][FONT=Calibri]Thanks[/FONT][/SIZE]

---

### Post by albandy on 2012-10-08
replace \ for /
./testapp

---

