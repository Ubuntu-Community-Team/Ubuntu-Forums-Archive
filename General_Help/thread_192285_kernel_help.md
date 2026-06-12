---
title: "kernel help"
date: 2006-06-08
forum: General Help
---

### Post by adolfotregosa on 2006-06-08
why do i get this error when i try "sudo make" ?? 

/usr/src/linux$ sudo make
Makefile:490: .config: No such file or directory
  CHK     include/linux/version.h
  HOSTCC  scripts/basic/split-include
In file included from /usr/include/linux/errno.h:4,
                 from /usr/include/bits/errno.h:25,
                 from /usr/include/errno.h:36,
                 from scripts/basic/split-include.c:26:
/usr/include/asm/errno.h:4:31: error: asm-generic/errno.h: No such file or directory
make[2]: *** [scripts/basic/split-include] Error 1
make[1]: *** [scripts_basic] Error 2
make: *** [include/linux/autoconf.h] Error 2

thanks

---

### Post by Sutekh on 2006-06-09
Have you installed *make?*  It's part of the meta-package - *build-essential*
```
sudo apt-get install build-essential
```
Then try *make* again, generally you don't need to use *sudo make*.

---

### Post by adolfotregosa on 2006-06-09
yes i did , anymore ideas ?

---

### Post by Sutekh on 2006-06-09
What are you trying to do?

Are you compiling a kernel, kernel module or something else?

---

### Post by adolfotregosa on 2006-06-09
i'm trying to install paragon ntfs driver. so when i try to install it says my kernel is not compiled. i'm trying to compile the kernel :S

""ntfslin_drv$ sudo sh install.sh
Can't find compiled modules for kernel 2.6.15.7-ubuntu1
Can't find compiled modules for kernel. Please, compile your kernel and run this program again.""

---

### Post by Sutekh on 2006-06-09
Ok, I should have asked before, can you link whatever guide/instructions you are following?

---

### Post by adolfotregosa on 2006-06-09
thank you but i managed to track down the error! it works fine now. I can read /write in ntfs :) ! finally

---

### Post by Sutekh on 2006-06-09
Sure no problem, I don't think I really did anything, it was all you!

---

