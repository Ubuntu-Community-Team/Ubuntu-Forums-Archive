---
title: "which one should I install ?"
date: 2010-05-01
forum: General Help
---

### Post by ibrahim.k on 2010-05-01
Hi,

I want to install 10.4 on my laptop
H-P dv6 1045ee

I don't know what the difference between 

amd64.iso
i386.iso

?

---

### Post by zengzhangsong on 2010-05-01
OK!I think i can tell you smoe differents between them.
the *amd64.iso is for 64bit AMD CPU and the *i386.iso is for 32bit CPU

---

### Post by ibrahim.k on 2010-05-01
my cpu is intel so I must download the 32 bit ?

---

### Post by robvas on 2010-05-01
What CPU do you have? 64-bit intel CPU will run AMD64 code.

---

### Post by The Real Dave on 2010-05-01
Your computer is 64bit capable [You've a Core2Duo as far as I can tell], and to get the best performance, you should use the 64bit [AMD64] version. 

64 or 32 bit has nothing to do with whether your CPU is Intel or AMD. Older computers used 32bit CPUs, and in some cases, could not recognise more than 3.7Gb of RAM. [32bit now can recognize more thanks to PAE]. 64bit removes that and other limitations. Newer [>2005] computers are generally 64Bit capable, even my 4 y/o Pentium IV runs 64bit Ubuntu happily. I barely notice the difference, other than the performance. Things like Video Encoding work much better on 64Bit. There are few differences on the software side between 32bit and 64bit Ubuntu, they both behave, look and practically are the same. The magic is in the inner workings ;)

---

### Post by ibrahim.k on 2010-05-01
Thank you very much :) I will install the amd64 version

---

### Post by Naitsirhc Hsem on 2010-05-01
amd 64bit utilises only 64bit processors and supports more than 3 gigs of ram. 32bit only supports 3 gigs of ram.  it all depends on your machine.  also not all programs run on 64-bit OS's

---

### Post by dino99 on 2010-05-01
there is more issues with 64 bits as some apps are not built for. Better to install i386 kernel with pae choice if you have >=4 go

---

### Post by The Real Dave on 2010-05-01
> **dino99 said:**
> there is more issues with 64 bits as some apps are not built for. Better to install i386 kernel with pae choice if you have >=4 go

For the average user, there's very little difference. Most applications these days support 64bit.

---

### Post by petex on 2010-05-04
I have been using x64 since 8.10 (I've been upgrading so far so stayed on x64)Now i will do new install and I'm wondering whether to go back to 32bit or 64 bit with 10.04 
the thing is using x64 requires adding 32 libs for some programs and generally speaking more hussle so do you guys think  the preformance gain is really worth it ??
I have asus n80vn -core 2 duo and 4GB of ram so just a bit more RAM gain over 32bit and with PAE even that is not an issue (even though PAE is supposed to be slower than full x64)

Addtional Q: did adobe finally gdeliver x64 flash ?

---

