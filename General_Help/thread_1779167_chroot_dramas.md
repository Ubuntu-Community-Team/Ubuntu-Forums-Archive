---
title: "chroot dramas"
date: 2011-06-10
forum: General Help
---

### Post by duschl on 2011-06-10
Hi, 
I am trying to make my ocz pci express work.  At this stage in the process I cannot chroot, I get the error /bin/bash not found. Following up various threads on the internet - this is common.  I think the problem in my case is the following: 
Issuing $ldd /bin/bash gives
    linux-vdso.so.1 =>  (0x00007fff34de7000)
    libncurses.so.5 => /lib/libncurses.so.5 (0x00007f82cb3b5000)
    libdl.so.2 => /lib/x86_64-linux-gnu/libdl.so.2 (0x00007f82cb1b1000)
    libc.so.6 => /lib/x86_64-linux-gnu/libc.so.6 (0x00007f82cae1c000)
    /lib64/ld-linux-x86-64.so.2 (0x00007f82cb619000)

I can locate all files and copy them into the lib directory I need to chroot from but not the first file "linux-vdso.so.1".  

I think this may be the reason why chroot doesn't work.  

Any suggestions? 

Ta, 
duschl

---

