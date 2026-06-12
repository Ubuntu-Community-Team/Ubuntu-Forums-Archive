---
title: "Asking help for compiling OpenSSL"
date: 2010-06-08
forum: General Help
---

### Post by zolero on 2010-06-08
Hi everyone there.

I am trying to upgrade my Hardy system's (don't switched to Lucid yet) SSL libraries by using Lucid source building with debhelper. Ubuntu patching, quilt-ing works perfect. Build seems to work also fine, but at some point I get this below, and I'm going stuck with it:

```
make[3]: Leaving directory `/home/zolero/builder/openssl-0.9.8k/crypto/des'
making all in crypto/aes...
make[3]: Entering directory `/home/zolero/builder/openssl-0.9.8k/crypto/aes'
cc -I.. -I../.. -I../../include -fPIC -DOPENSSL_PIC -DZLIB -DOPENSSL_THREADS -D_REENTRANT -DDSO_DLFCN -DHAVE_DLFCN_H -DL_ENDIAN -DTERMIO -O3 -march=i486 -Wa,--noexecstack -g -Wall -DOPENSSL_BN_ASM_PART_WORDS -DOPENSSL_IA32_SSE2 -DSHA1_ASM -DMD5_ASM -DRMD160_ASM -DAES_ASM   -c -o aes_misc.o aes_misc.c
cc -I.. -I../.. -I../../include -fPIC -DOPENSSL_PIC -DZLIB -DOPENSSL_THREADS -D_REENTRANT -DDSO_DLFCN -DHAVE_DLFCN_H -DL_ENDIAN -DTERMIO -O3 -march=i486 -Wa,--noexecstack -g -Wall -DOPENSSL_BN_ASM_PART_WORDS -DOPENSSL_IA32_SSE2 -DSHA1_ASM -DMD5_ASM -DRMD160_ASM -DAES_ASM   -c -o aes_ecb.o aes_ecb.c
cc -I.. -I../.. -I../../include -fPIC -DOPENSSL_PIC -DZLIB -DOPENSSL_THREADS -D_REENTRANT -DDSO_DLFCN -DHAVE_DLFCN_H -DL_ENDIAN -DTERMIO -O3 -march=i486 -Wa,--noexecstack -g -Wall -DOPENSSL_BN_ASM_PART_WORDS -DOPENSSL_IA32_SSE2 -DSHA1_ASM -DMD5_ASM -DRMD160_ASM -DAES_ASM   -c -o aes_cfb.o aes_cfb.c
cc -I.. -I../.. -I../../include -fPIC -DOPENSSL_PIC -DZLIB -DOPENSSL_THREADS -D_REENTRANT -DDSO_DLFCN -DHAVE_DLFCN_H -DL_ENDIAN -DTERMIO -O3 -march=i486 -Wa,--noexecstack -g -Wall -DOPENSSL_BN_ASM_PART_WORDS -DOPENSSL_IA32_SSE2 -DSHA1_ASM -DMD5_ASM -DRMD160_ASM -DAES_ASM   -c -o aes_ofb.o aes_ofb.c
cc -I.. -I../.. -I../../include -fPIC -DOPENSSL_PIC -DZLIB -DOPENSSL_THREADS -D_REENTRANT -DDSO_DLFCN -DHAVE_DLFCN_H -DL_ENDIAN -DTERMIO -O3 -march=i486 -Wa,--noexecstack -g -Wall -DOPENSSL_BN_ASM_PART_WORDS -DOPENSSL_IA32_SSE2 -DSHA1_ASM -DMD5_ASM -DRMD160_ASM -DAES_ASM   -c -o aes_ctr.o aes_ctr.c
cc -I.. -I../.. -I../../include -fPIC -DOPENSSL_PIC -DZLIB -DOPENSSL_THREADS -D_REENTRANT -DDSO_DLFCN -DHAVE_DLFCN_H -DL_ENDIAN -DTERMIO -O3 -march=i486 -Wa,--noexecstack -g -Wall -DOPENSSL_BN_ASM_PART_WORDS -DOPENSSL_IA32_SSE2 -DSHA1_ASM -DMD5_ASM -DRMD160_ASM -DAES_ASM   -c -o aes_ige.o aes_ige.c
cc -I.. -I../.. -I../../include -fPIC -DOPENSSL_PIC -DZLIB -DOPENSSL_THREADS -D_REENTRANT -DDSO_DLFCN -DHAVE_DLFCN_H -DL_ENDIAN -DTERMIO -O3 -march=i486 -Wa,--noexecstack -g -Wall -DOPENSSL_BN_ASM_PART_WORDS -DOPENSSL_IA32_SSE2 -DSHA1_ASM -DMD5_ASM -DRMD160_ASM -DAES_ASM   -c -o aes_wrap.o aes_wrap.c
(cd asm; /usr/bin/perl aes-586.pl elf -I.. -I../.. -I../../include -fPIC -DOPENSSL_PIC -DZLIB -DOPENSSL_THREADS -D_REENTRANT -DDSO_DLFCN -DHAVE_DLFCN_H -DL_ENDIAN -DTERMIO -O3 -march=i486 -Wa,--noexecstack -g -Wall -DOPENSSL_BN_ASM_PART_WORDS -DOPENSSL_IA32_SSE2 -DSHA1_ASM -DMD5_ASM -DRMD160_ASM -DAES_ASM  > ../ax86-elf.s)
cc -I.. -I../.. -I../../include -fPIC -DOPENSSL_PIC -DZLIB -DOPENSSL_THREADS -D_REENTRANT -DDSO_DLFCN -DHAVE_DLFCN_H -DL_ENDIAN -DTERMIO -O3 -march=i486 -Wa,--noexecstack -g -Wall -DOPENSSL_BN_ASM_PART_WORDS -DOPENSSL_IA32_SSE2 -DSHA1_ASM -DMD5_ASM -DRMD160_ASM -DAES_ASM -c  -o ax86-elf.o ax86-elf.s
(cd asm; /usr/bin/perl aesni-x86.pl elf -I.. -I../.. -I../../include -fPIC -DOPENSSL_PIC -DZLIB -DOPENSSL_THREADS -D_REENTRANT -DDSO_DLFCN -DHAVE_DLFCN_H -DL_ENDIAN -DTERMIO -O3 -march=i486 -Wa,--noexecstack -g -Wall -DOPENSSL_BN_ASM_PART_WORDS -DOPENSSL_IA32_SSE2 -DSHA1_ASM -DMD5_ASM -DRMD160_ASM -DAES_ASM  > ../nx86-elf.s)
cc -I.. -I../.. -I../../include -fPIC -DOPENSSL_PIC -DZLIB -DOPENSSL_THREADS -D_REENTRANT -DDSO_DLFCN -DHAVE_DLFCN_H -DL_ENDIAN -DTERMIO -O3 -march=i486 -Wa,--noexecstack -g -Wall -DOPENSSL_BN_ASM_PART_WORDS -DOPENSSL_IA32_SSE2 -DSHA1_ASM -DMD5_ASM -DRMD160_ASM -DAES_ASM -c  -o nx86-elf.o nx86-elf.s
nx86-elf.s: Assembler messages:
nx86-elf.s:18: Error: no such instruction: `aesenc %xmm4,%xmm0'
nx86-elf.s:23: Error: no such instruction: `aesenclast %xmm4,%xmm0'
nx86-elf.s:42: Error: no such instruction: `aesdec %xmm4,%xmm0'
nx86-elf.s:47: Error: no such instruction: `aesdeclast %xmm4,%xmm0'
nx86-elf.s:64: Error: no such instruction: `aesenc %xmm4,%xmm0'
nx86-elf.s:66: Error: no such instruction: `aesenc %xmm4,%xmm1'
nx86-elf.s:68: Error: no such instruction: `aesenc %xmm4,%xmm2'
nx86-elf.s:70: Error: no such instruction: `aesenc %xmm3,%xmm0'
nx86-elf.s:72: Error: no such instruction: `aesenc %xmm3,%xmm1'
nx86-elf.s:73: Error: no such instruction: `aesenc %xmm3,%xmm2'
nx86-elf.s:75: Error: no such instruction: `aesenc %xmm4,%xmm0'
nx86-elf.s:77: Error: no such instruction: `aesenc %xmm4,%xmm1'
nx86-elf.s:78: Error: no such instruction: `aesenc %xmm4,%xmm2'
nx86-elf.s:79: Error: no such instruction: `aesenclast %xmm3,%xmm0'
nx86-elf.s:80: Error: no such instruction: `aesenclast %xmm3,%xmm1'
nx86-elf.s:81: Error: no such instruction: `aesenclast %xmm3,%xmm2'
nx86-elf.s:97: Error: no such instruction: `aesdec %xmm4,%xmm0'
nx86-elf.s:99: Error: no such instruction: `aesdec %xmm4,%xmm1'
nx86-elf.s:101: Error: no such instruction: `aesdec %xmm4,%xmm2'
nx86-elf.s:103: Error: no such instruction: `aesdec %xmm3,%xmm0'
nx86-elf.s:105: Error: no such instruction: `aesdec %xmm3,%xmm1'
nx86-elf.s:106: Error: no such instruction: `aesdec %xmm3,%xmm2'
nx86-elf.s:108: Error: no such instruction: `aesdec %xmm4,%xmm0'
nx86-elf.s:110: Error: no such instruction: `aesdec %xmm4,%xmm1'
nx86-elf.s:111: Error: no such instruction: `aesdec %xmm4,%xmm2'
nx86-elf.s:112: Error: no such instruction: `aesdeclast %xmm3,%xmm0'
nx86-elf.s:113: Error: no such instruction: `aesdeclast %xmm3,%xmm1'
nx86-elf.s:114: Error: no such instruction: `aesdeclast %xmm3,%xmm2'
nx86-elf.s:131: Error: no such instruction: `aesenc %xmm4,%xmm0'
nx86-elf.s:133: Error: no such instruction: `aesenc %xmm4,%xmm1'
nx86-elf.s:135: Error: no such instruction: `aesenc %xmm4,%xmm2'
nx86-elf.s:136: Error: no such instruction: `aesenc %xmm4,%xmm7'
nx86-elf.s:138: Error: no such instruction: `aesenc %xmm3,%xmm0'
nx86-elf.s:140: Error: no such instruction: `aesenc %xmm3,%xmm1'
nx86-elf.s:141: Error: no such instruction: `aesenc %xmm3,%xmm2'
nx86-elf.s:142: Error: no such instruction: `aesenc %xmm3,%xmm7'
nx86-elf.s:144: Error: no such instruction: `aesenc %xmm4,%xmm0'
nx86-elf.s:146: Error: no such instruction: `aesenc %xmm4,%xmm1'
nx86-elf.s:147: Error: no such instruction: `aesenc %xmm4,%xmm2'
nx86-elf.s:148: Error: no such instruction: `aesenc %xmm4,%xmm7'
nx86-elf.s:149: Error: no such instruction: `aesenclast %xmm3,%xmm0'
nx86-elf.s:150: Error: no such instruction: `aesenclast %xmm3,%xmm1'
nx86-elf.s:151: Error: no such instruction: `aesenclast %xmm3,%xmm2'
nx86-elf.s:152: Error: no such instruction: `aesenclast %xmm3,%xmm7'
nx86-elf.s:169: Error: no such instruction: `aesdec %xmm4,%xmm0'
nx86-elf.s:171: Error: no such instruction: `aesdec %xmm4,%xmm1'
nx86-elf.s:173: Error: no such instruction: `aesdec %xmm4,%xmm2'
nx86-elf.s:174: Error: no such instruction: `aesdec %xmm4,%xmm7'
nx86-elf.s:176: Error: no such instruction: `aesdec %xmm3,%xmm0'
nx86-elf.s:178: Error: no such instruction: `aesdec %xmm3,%xmm1'
nx86-elf.s:179: Error: no such instruction: `aesdec %xmm3,%xmm2'
nx86-elf.s:180: Error: no such instruction: `aesdec %xmm3,%xmm7'
nx86-elf.s:182: Error: no such instruction: `aesdec %xmm4,%xmm0'
nx86-elf.s:184: Error: no such instruction: `aesdec %xmm4,%xmm1'
nx86-elf.s:185: Error: no such instruction: `aesdec %xmm4,%xmm2'
nx86-elf.s:186: Error: no such instruction: `aesdec %xmm4,%xmm7'
nx86-elf.s:187: Error: no such instruction: `aesdeclast %xmm3,%xmm0'
nx86-elf.s:188: Error: no such instruction: `aesdeclast %xmm3,%xmm1'
nx86-elf.s:189: Error: no such instruction: `aesdeclast %xmm3,%xmm2'
nx86-elf.s:190: Error: no such instruction: `aesdeclast %xmm3,%xmm7'
nx86-elf.s:259: Error: no such instruction: `aesenc %xmm4,%xmm0'
nx86-elf.s:264: Error: no such instruction: `aesenclast %xmm4,%xmm0'
nx86-elf.s:326: Error: no such instruction: `aesdec %xmm4,%xmm0'
nx86-elf.s:331: Error: no such instruction: `aesdeclast %xmm4,%xmm0'
nx86-elf.s:390: Error: no such instruction: `aesenc %xmm4,%xmm0'
nx86-elf.s:395: Error: no such instruction: `aesenclast %xmm4,%xmm0'
nx86-elf.s:479: Error: no such instruction: `aesdec %xmm4,%xmm0'
nx86-elf.s:484: Error: no such instruction: `aesdeclast %xmm4,%xmm0'
nx86-elf.s:550: Error: no such instruction: `aeskeygenassist $1,%xmm0,%xmm1'
nx86-elf.s:552: Error: no such instruction: `aeskeygenassist $2,%xmm0,%xmm1'
nx86-elf.s:554: Error: no such instruction: `aeskeygenassist $4,%xmm0,%xmm1'
nx86-elf.s:556: Error: no such instruction: `aeskeygenassist $8,%xmm0,%xmm1'
nx86-elf.s:558: Error: no such instruction: `aeskeygenassist $16,%xmm0,%xmm1'
nx86-elf.s:560: Error: no such instruction: `aeskeygenassist $32,%xmm0,%xmm1'
nx86-elf.s:562: Error: no such instruction: `aeskeygenassist $64,%xmm0,%xmm1'
nx86-elf.s:564: Error: no such instruction: `aeskeygenassist $128,%xmm0,%xmm1'
nx86-elf.s:566: Error: no such instruction: `aeskeygenassist $27,%xmm0,%xmm1'
nx86-elf.s:568: Error: no such instruction: `aeskeygenassist $54,%xmm0,%xmm1'
nx86-elf.s:591: Error: no such instruction: `aeskeygenassist $1,%xmm2,%xmm1'
nx86-elf.s:593: Error: no such instruction: `aeskeygenassist $2,%xmm2,%xmm1'
nx86-elf.s:595: Error: no such instruction: `aeskeygenassist $4,%xmm2,%xmm1'
nx86-elf.s:597: Error: no such instruction: `aeskeygenassist $8,%xmm2,%xmm1'
nx86-elf.s:599: Error: no such instruction: `aeskeygenassist $16,%xmm2,%xmm1'
nx86-elf.s:601: Error: no such instruction: `aeskeygenassist $32,%xmm2,%xmm1'
nx86-elf.s:603: Error: no such instruction: `aeskeygenassist $64,%xmm2,%xmm1'
nx86-elf.s:605: Error: no such instruction: `aeskeygenassist $128,%xmm2,%xmm1'
nx86-elf.s:647: Error: no such instruction: `aeskeygenassist $1,%xmm2,%xmm1'
nx86-elf.s:649: Error: no such instruction: `aeskeygenassist $1,%xmm0,%xmm1'
nx86-elf.s:651: Error: no such instruction: `aeskeygenassist $2,%xmm2,%xmm1'
nx86-elf.s:653: Error: no such instruction: `aeskeygenassist $2,%xmm0,%xmm1'
nx86-elf.s:655: Error: no such instruction: `aeskeygenassist $4,%xmm2,%xmm1'
nx86-elf.s:657: Error: no such instruction: `aeskeygenassist $4,%xmm0,%xmm1'
nx86-elf.s:659: Error: no such instruction: `aeskeygenassist $8,%xmm2,%xmm1'
nx86-elf.s:661: Error: no such instruction: `aeskeygenassist $8,%xmm0,%xmm1'
nx86-elf.s:663: Error: no such instruction: `aeskeygenassist $16,%xmm2,%xmm1'
nx86-elf.s:665: Error: no such instruction: `aeskeygenassist $16,%xmm0,%xmm1'
nx86-elf.s:667: Error: no such instruction: `aeskeygenassist $32,%xmm2,%xmm1'
nx86-elf.s:669: Error: no such instruction: `aeskeygenassist $32,%xmm0,%xmm1'
nx86-elf.s:671: Error: no such instruction: `aeskeygenassist $64,%xmm2,%xmm1'
nx86-elf.s:743: Error: no such instruction: `aesimc %xmm0,%xmm0'
nx86-elf.s:744: Error: no such instruction: `aesimc %xmm1,%xmm1'
nx86-elf.s:752: Error: no such instruction: `aesimc %xmm0,%xmm0'
make[3]: *** [nx86-elf.o] Error 1
make[3]: Leaving directory `/home/zolero/builder/openssl-0.9.8k/crypto/aes'
make[2]: *** [subdirs] Error 1
make[2]: Leaving directory `/home/zolero/builder/openssl-0.9.8k/crypto'
make[1]: *** [build_crypto] Error 1
make[1]: Leaving directory `/home/zolero/builder/openssl-0.9.8k'
make: *** [build-stamp] Error 2
zolero@bluestorm:~/builder/openssl-0.9.8k$
```

Question(s): Did anyone managed to build an OpenSSL package above the "i" version on Hardy (well, or at least not in its default distrib edition - aka upgrade)?
Had anyone encountered this error, and how do you solve it?

Any help will be greatly appreciated. Thanks in advance, Z.

---

### Post by zolero on 2010-06-09
Bump.  Hey, nobody knows this?  Unbelievable.

---

### Post by zolero on 2010-06-11
Never mind... I've managed to build it. The "aesni.patch" in the quilt series was the evil there. Replaced with another AES-NI Intel instructions patch and gotcha...  ;)

Add: As a hint (because don't remind where I've get that patch) it needs x86_64 AES-NI support to build on multicore SMP processors (like mine Core2 Duo E4700). Or even better, I attach here the patch that I worked a bit to match with openssl-0.9.8k, if anyone is interested to build newer OpenSSL on older editions than Lucid.

---

