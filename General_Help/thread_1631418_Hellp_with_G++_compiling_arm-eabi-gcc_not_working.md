---
title: "Hellp with G++ compiling arm-eabi-gcc not working"
date: 2010-11-26
forum: General Help
---

### Post by whatnissan on 2010-11-26
Well I have started work on compiling tun.ko for the mytouch 4g so we can use openvpn on these phones. Its all ready to go but i cant get 
arm-eabi-gcc to work on Ubuntu the way its supposed to. Any help would be great here is my error out put. 


user@ubuntu:~/Documents/Android1/glacier-2.6.32-g52a2a81$ make modules CHK include/linux/version.h
make[1]: `include/asm-arm/mach-types.h' is up to date.
CHK include/linux/utsrelease.h
SYMLINK include/asm -> include/asm-arm
CC kernel/bounds.s
arm-eabi-gcc: error trying to exec 'cc1': execvp: No such file or directory
make[1]: *** [kernel/bounds.s] Error 1
make: *** [prepare0] Error 2
user@ubuntu:~/Documents/Android1/glacier-2.6.32-g52a2a81$ make modules
CHK include/linux/version.h
make[1]: `include/asm-arm/mach-types.h' is up to date.
CHK include/linux/utsrelease.h
SYMLINK include/asm -> include/asm-arm
CC kernel/bounds.s
arm-eabi-gcc: error trying to exec 'cc1': execvp: No such file or directory
make[1]: *** [kernel/bounds.s] Error 1
make: *** [prepare0] Error 2

any ideas????
also when I do the g++ -o hello.o hello.cpp i get 

dlafortune@ubuntu:~/Documents/Android1/glacier-2.6.32-g52a2a81$ g++ -o hello.o hello.cpp
g++: hello.cpp: No such file or directory
g++: no input files

---

