---
title: "How to know the version of ubuntu in your system?"
date: 2010-11-13
forum: General Help
---

### Post by Lancro on 2010-11-13
I dont mean maverick or whatever, thats in about ubuntu, I mean 32 bits or 64 bits, I dont really know what of both I have, my first ubuntu was installed inside windows with wubi, It was 10.04, my windows was 64 bits, then I upgraded to 10.10 and then I put that in a partition using a tutorial, It detects 3.9 GiB of RAM, so I think its the 64 version, because 32 bits in theory cant manage more than 3 GiB, but I want to see it clearly, if Im using 32 or 64 bits ubuntu.

Thanks.

---

### Post by CharlesA on 2010-11-13
Run this:

```
uname -a
```

i386 or i686 = 32-bit
x64_86 = 64-bit

Max memory doesn't really matter, since Ubuntu will install the PAE kernel if you are installing the 32-bit version with more then 4GB of RAM.

---

### Post by brydonhunter on 2010-11-13
```
cat /etc/issue
```

---

### Post by bilalsana on 2010-11-13
go to 


System > About Ubuntu

---

### Post by efflandt on 2010-11-13
cat /etc/*release

Oops, brydenhunter and I should have read more carefully. CharlesA is right.

---

### Post by Lancro on 2010-11-13
> **CharlesA said:**
> Run this:

```
uname -a
```i386 or i686 = 32-bit
x64_86 = 64-bit

Max memory doesn't really matter, since Ubuntu will install the PAE kernel if you are installing the 32-bit version with more then 4GB of RAM.

```
Linux ubuntu 2.6.35-22-generic #35-Ubuntu SMP Sat Oct 16 20:45:36 UTC 2010 x86_64 GNU/Linux
```

Its not x64_86 but its x86_64, so Its 64 bits, thanks.

---

