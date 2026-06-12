---
title: "libssh-0.11 make fails"
date: 2009-08-12
forum: General Help
---

### Post by t0p on 2009-08-12
I need to install [libssh-0.11]("http://nixbit.com/cat/system/networking/ssh-library/") so I can then install [thc-hydra]("http://freeworld.thc.org/thc-hydra/") with ssh support.  **./configure** goes okay, but then **make** fails:

```
t0p@machine:~/Desktop/libssh-0.11$ make
gcc -g -O2 -Iinclude/ -Wall -g   -c -o sample.o sample.c
sample.c: In function ‘select_loop’:
sample.c:153: warning: ignoring return value of ‘write’, declared with attribute warn_unused_result
sample.c:164: warning: ignoring return value of ‘write’, declared with attribute warn_unused_result
sample.c: In function ‘auth_kbdint’:
sample.c:306: warning: ignoring return value of ‘fgets’, declared with attribute warn_unused_result
sample.c: In function ‘main’:
sample.c:356: warning: pointer targets in passing argument 2 of ‘ssh_print_hexa’ differ in signedness
sample.c:370: warning: pointer targets in passing argument 2 of ‘ssh_print_hexa’ differ in signedness
sample.c:371: warning: ignoring return value of ‘fgets’, declared with attribute warn_unused_result
sample.c:377: warning: ignoring return value of ‘fgets’, declared with attribute warn_unused_result
gcc -g -O2 -Iinclude/ -Wall -g   -c -o samplesshd.o samplesshd.c
make[1]: Entering directory `/home/t0p/Desktop/libssh-0.11/libssh'
gcc -g -O2 -Wall -g -I../include/ -fPIC   -c -o client.o client.c
In file included from client.c:27:
../include/libssh/priv.h:58:25: error: openssl/dsa.h: No such file or directory
../include/libssh/priv.h:59:25: error: openssl/rsa.h: No such file or directory
../include/libssh/priv.h:60:25: error: openssl/sha.h: No such file or directory
../include/libssh/priv.h:61:25: error: openssl/md5.h: No such file or directory
../include/libssh/priv.h:62:26: error: openssl/hmac.h: No such file or directory
In file included from client.c:27:
../include/libssh/priv.h:63: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘SHACTX’
../include/libssh/priv.h:64: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘MD5CTX’
../include/libssh/priv.h:65: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘HMACCTX’
../include/libssh/priv.h:74:24: error: openssl/bn.h: No such file or directory
../include/libssh/priv.h:75: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
../include/libssh/priv.h:76: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
In file included from client.c:27:
../include/libssh/priv.h:98: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
../include/libssh/priv.h:99: error: expected ‘)’ before ‘*’ token
../include/libssh/priv.h:100: error: expected declaration specifiers or ‘...’ before ‘MD5CTX’
../include/libssh/priv.h:101: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
../include/libssh/priv.h:102: error: expected ‘)’ before ‘*’ token
../include/libssh/priv.h:103: error: expected declaration specifiers or ‘...’ before ‘SHACTX’
../include/libssh/priv.h:107: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
../include/libssh/priv.h:108: error: expected ‘)’ before ‘*’ token
../include/libssh/priv.h:109: error: expected ‘)’ before ‘*’ token
../include/libssh/priv.h:141: error: expected specifier-qualifier-list before ‘DSA’
../include/libssh/priv.h:147: error: expected specifier-qualifier-list before ‘DSA’
../include/libssh/priv.h:153: error: expected specifier-qualifier-list before ‘DSA_SIG’
../include/libssh/priv.h:179: error: expected specifier-qualifier-list before ‘bignum’
../include/libssh/priv.h:279: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘make_string_bn’
../include/libssh/priv.h:280: error: expected ‘)’ before ‘num’
../include/libssh/priv.h:368: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘BN_new’
client.c: In function ‘ssh_send_banner’:
client.c:67: warning: ignoring return value of ‘write’, declared with attribute warn_unused_result
make[1]: *** [client.o] Error 1
make[1]: Leaving directory `/home/t0p/Desktop/libssh-0.11/libssh'
make: *** [all] Error 1
t0p@machine:~/Desktop/libssh-0.11$ 

```

I have no idea how to rectify this.  Can anyone advise?

---

### Post by mc4man on 2009-08-12
make sure you have libssl-dev installed

---

### Post by r1dw4n on 2009-10-13
I installing libssh from sourcecode. 
I cant ./configure libssh, it's need openssl or libgcrypt prefix. 

any one can resolve ?

---

