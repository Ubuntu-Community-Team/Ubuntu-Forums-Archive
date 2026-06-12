---
title: "can someone help plz"
date: 2010-01-30
forum: General Help
---

### Post by slaapp on 2010-01-30
i was doing a compile  it was  going good then i got this

 /usr/bin/ld: skipping incompatible /usr/lib/gcc/x86_64-linux-gnu/4.3.3/../../../libelf.so when searching for -lelf
/usr/bin/ld: skipping incompatible /usr/lib/gcc/x86_64-linux-gnu/4.3.3/../../../libelf.a when searching for -lelf
/usr/bin/ld: skipping incompatible /usr/lib/libelf.so when searching for -lelf
/usr/bin/ld: skipping incompatible /usr/lib/libelf.a when searching for -lelf
/usr/bin/ld: cannot find -lelf

i use ubuntu 9.04 32 bit any help to fix this and how to fix thx:)

---

### Post by labinnsw on 2010-02-06
What are you compiling?
Is it a 32 bit or a 64 bit version?

Please also see my signature.

---

### Post by mushwars on 2010-02-06
looks like it cant find the elf library, you should apt-cache search elf and see if you can find what you need to install, that is the problem with compiling from source, you do not get the dependencies to install automatically.

---

