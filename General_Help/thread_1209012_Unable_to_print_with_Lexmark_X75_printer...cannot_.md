---
title: "Unable to print with Lexmark X75 printer...cannot install driver"
date: 2009-07-09
forum: General Help
---

### Post by cnateb on 2009-07-09
I was recently given a Lexmark X75 printer by my mother because she got a new printer and I have to load pages individually for my printer or it jams.

I have done quite a bit of research over the past few days on the Lexmark X75 to get it to work with Ubuntu.  I found a post that supposedly solved the problem from a few years ago on a different version of Ubuntu.  I tried that and got the following errors.

The solution I tried was at the following link:
[http://ubuntuforums.org/showthread.php?t=340735](http://ubuntuforums.org/showthread.php?t=340735)

nate@nate-desktop:~/Desktop/temp/lxx74-cups-0.8.4.2/lxx74-cups-0.8.4.2$ make
gcc -g -c rastertolxx74.c
rastertolxx74.c: In function ‘lxx74_print_page’:
rastertolxx74.c:1399: warning: format ‘%u’ expects type ‘unsigned int’, but argument 5 has type ‘off_t’
rastertolxx74.c:1399: warning: format ‘%u’ expects type ‘unsigned int’, but argument 6 has type ‘off_t’
rastertolxx74.c:1399: warning: format ‘%d’ expects type ‘int’, but argument 7 has type ‘off_t’
rastertolxx74.c:1450: warning: format ‘%u’ expects type ‘unsigned int’, but argument 5 has type ‘long unsigned int’
gcc -o rastertolxx74 rastertolxx74.o -lz -lcupsimage -lcups
nate@nate-desktop:~/Desktop/temp/lxx74-cups-0.8.4.2$ sudo make install
bash lxx74.install
lxx74.install: Error: Unable to locate the CUPS model directory (where the PPD files are stored).
Aborting.
make: *** [install] Error 1


I am running Ubuntu 8.10

I'm relatively new to Linux and am still learning, so please be nice if the problem is somewhat obvious.  

Any help on how to solve this would be greatly appreciated, or even a pointer in the right direction.  I've spent several days looking for an answer.  

Thanks,

Nate

---

### Post by cnateb on 2009-08-13
Decided to just throw printer away

---

