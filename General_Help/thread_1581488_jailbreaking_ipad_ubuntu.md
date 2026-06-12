---
title: "jailbreaking ipad ubuntu"
date: 2010-09-25
forum: General Help
---

### Post by Muggles on 2010-09-25
Hey, I've just recently switch to ubuntu as my sole os, I'm still working some stuff out. I've been following the instructions on  [http://www.packtpub.com/article/jailbreaking-ipad-in-ubuntu. ]("http://www.packtpub.com/article/jailbreaking-ipad-in-ubuntu")

   I've gotten up to the stage where it tells me to plug in my iPad, which I  can see but can't do anything with, it gives me the message "could not  display aft://" then a whole string of letters and numbers.
   In terminal I've tried running 
cd spirit-linux 
make
spirit

What I get is this

lucas@lucas-laptop:~$ cd spirit-linux
lucas@lucas-laptop:~/spirit-linux$ make
gcc -std=gnu99 -c -o spirit.o spirit.c
spirit.c:28:25: error: openssl/sha.h: No such file or directory
spirit.c: In function ‘sha1_of_data’:
spirit.c:59: error: ‘SHA_CTX’ undeclared (first use in this function)
spirit.c:59: error: (Each undeclared identifier is reported only once
spirit.c:59: error: for each function it appears in.)
spirit.c:59: error: expected ‘;’ before ‘ctx’
spirit.c:60: warning: implicit declaration of function ‘SHA1_Init’
spirit.c:60: error: ‘ctx’ undeclared (first use in this function)
spirit.c:61: warning: implicit declaration of function ‘SHA1_Update’
spirit.c:62: warning: implicit declaration of function ‘SHA1_Final’
spirit.c: In function ‘add_file’:
spirit.c:272: error: ‘SHA_CTX’ undeclared (first use in this function)
spirit.c:272: error: expected ‘;’ before ‘ctx’
spirit.c:273: error: ‘ctx’ undeclared (first use in this function)
make: *** [spirit.o] Error 1
lucas@lucas-laptop:~/spirit-linux$ spirit
spirit: command not found
lucas@lucas-laptop:~/spirit-linux$ ^C
lucas@lucas-laptop:~/spirit-linux$ 

   Not sure what I'm doing wrong. Any help much appreciated.

---

### Post by NickCis on 2010-09-27
Try installing libssl-dev ( sudo apt-get install libssl-dev ) and then compiling again.

I found that info here: [http://github.com/posixninja/spirit-linux/issues?locale=es#issue/10](http://github.com/posixninja/spirit-linux/issues?locale=es#issue/10)

Good luck :P

---

