---
title: "Arm cross compilation"
date: 2009-12-18
forum: General Help
---

### Post by shariefbe on 2009-12-18
Hello,
   I am trying to compile my kernel for ARM Processor. when i do that i am getting some following error. I didnt find what will be the problem.
```

root@ariem-desktop:/home/ariem/Desktop/kernels/linux-2.6.28-006rc8# make CROSS_COMPILE=/home/ariem/CodeSourcery/Sourcery_G++_Lite/bin/arm-none-linux-gnueabi- uImage
  CHK     include/linux/version.h
make[1]: `include/asm-arm/mach-types.h' is up to date.
  CHK     include/linux/utsrelease.h
  SYMLINK include/asm -> include/asm-arm
  CALL    scripts/checksyscalls.sh
<stdin>:1097:2: warning: #warning syscall fadvise64 not implemented
<stdin>:1265:2: warning: #warning syscall migrate_pages not implemented
<stdin>:1321:2: warning: #warning syscall pselect6 not implemented
<stdin>:1325:2: warning: #warning syscall ppoll not implemented
<stdin>:1365:2: warning: #warning syscall epoll_pwait not implemented
  CC      init/main.o
/tmp/cczCT0T5.s: Assembler messages:
/tmp/cczCT0T5.s:255: Error: selected processor does not support `cpsie i'
/tmp/cczCT0T5.s:704: Error: selected processor does not support `cpsid i'
/tmp/cczCT0T5.s:712: Error: selected processor does not support `cpsid i'
/tmp/cczCT0T5.s:726: Error: selected processor does not support `cpsid i'
/tmp/cczCT0T5.s:740: Error: selected processor does not support `cpsid i'
/tmp/cczCT0T5.s:812: Error: selected processor does not support `cpsid i'
/tmp/cczCT0T5.s:837: Error: selected processor does not support `cpsie i'
make[1]: *** [init/main.o] Error 1
make: *** [init] Error 2
root@ariem-desktop:/home/ariem/Desktop/kernels/linux-2.6.28-006rc8# 


```
Kindly help me

---

