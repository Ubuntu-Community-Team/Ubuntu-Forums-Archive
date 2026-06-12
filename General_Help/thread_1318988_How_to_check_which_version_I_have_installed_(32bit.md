---
title: "How to check which version I have installed (32bit or 64bit)?"
date: 2009-11-08
forum: General Help
---

### Post by bullka on 2009-11-08
Command "uname -m" gives result:

x86_64

I think x86 refers to 32bit and 64 to 64bit. So which version is installed in my PC?

---

### Post by The Funkbomb on 2009-11-08
64bit

---

### Post by squenson on 2009-11-08
x86 refers o the type of processor, in your case Intel.They were called 286, 386, 486 then Intel changed to pentium instead of 586 and I guess the last generation has the prefix 6. x86 has no information about the type of the OS, 32 or 64 bits.

---

### Post by bullka on 2009-11-08
What result would uname -m give in 32bit systems in that case?

x86_32

??

---

### Post by Vernünftiger Verbrecher on 2009-11-08
I prefer the programmer's method. In c just type "printf("i%\n", sizeof(i));" and it will either return 4 or 8, which is in bytes. Then you just multiply the result by 8, since there are 8 bits in one byte and you get 32 for 4 and 64 for 8.

---

### Post by ww711 on 2009-11-08
> **bullka said:**
> What result would uname -m give in 32bit systems in that case?

x86_32

??

It would probably display i686 if it was a newer system, run ```
uname-m
``` on your system, this will give you the information.

---

### Post by Darce on 2009-11-08
uname -m returns 'i686' for me. Don't think its anything to do with the OS being 32/64 bit

Try uname --help or man uname for for the destructions, but I dont think any switches will tell you what you want to know.....

---

### Post by priegog on 2009-11-08
> **Darce said:**
> uname -m returns 'i686' for me. Don't think its anything to do with the OS being 32/64 bit

i686 is 32-bit
x86_64 is 64 bits

I think there are a few other ways that 32 bit architecture is referred to, but the most common is i686.
Let's not make a mess out of something so simple.

---

### Post by bullka on 2009-11-08
> **priegog said:**
> i686 is 32-bit
x86_64 is 64 bits

I think there are a few other ways that 32 bit architecture is referred to, but the most common is i686.
Let's not make a mess out of something so simple.

Just tested with a 32bit Ubuntu running in vmware. The result of the command uname -m is:

i686

Thanks for help!!!!

---

