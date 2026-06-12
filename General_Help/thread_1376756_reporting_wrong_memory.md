---
title: "reporting wrong memory"
date: 2010-01-09
forum: General Help
---

### Post by Mia_tech on 2010-01-09
guys, I have a system which has 6 G of RAM, and Ubuntu is only reporting 3.2.... what could be the problem here?


thanks

---

### Post by oldos2er on 2010-01-09
If you're using 32-bit Ubuntu, that's normal. For Ubuntu to use all your RAM, you'll need to either install 64-bit, or install a PAE kernel.

---

### Post by 73ckn797 on 2010-01-09
The PAE kernel is found in Synaptic.

---

### Post by dcstar on 2010-01-10
> **oldos2er said:**
> If you're using 32-bit Ubuntu, that's normal. For Ubuntu to use all your RAM, you'll need to either install 64-bit, or install a PAE kernel.

And understand that any single 32-bit process can only ever use 4GB maximum - all PAE does is allow other processes to use/access RAM in up to 4GB chunks (and at a performance hit if memory has to be shared).

---

### Post by Mia_tech on 2010-01-10
> **dcstar said:**
> And understand that any single 32-bit process can only ever use 4GB maximum - all PAE does is allow other processes to use/access RAM in up to 4GB chunks (and at a performance hit if memory has to be shared).

yes, I was aware of OS 32=4G and 64=128G, but the thing that threw me off was the rare number reported by the OS, which is 3.2. Now, one of the draw back of 64 is the lack of support of drivers and applications...

---

### Post by lotharmat on 2010-01-10
> **Mia_tech said:**
> yes, I was aware of OS 32=4G and 64=128G, but the thing that threw me off was the rare number reported by the OS, which is 3.2. Now, one of the draw back of 64 is the lack of support of drivers and applications...

Ubuntu 32 bit will only ever report 3.2 gig evAr

---

### Post by NoaHall on 2010-01-10
> **Mia_tech said:**
> yes, I was aware of OS 32=4G and 64=128G, but the thing that threw me off was the rare number reported by the OS, which is 3.2. Now, one of the draw back of 64 is the lack of support of drivers and applications...

There is no draw back from 64 bit now days. It's better supported than 32 bit, in some cases. And there are no drivers that you can't install on 64 bit, as far as I know.

---

### Post by oldos2er on 2010-01-10
> **Mia_tech said:**
> one of the draw back of 64 is the lack of support of drivers and applications...

Can't say I've noticed that.

---

### Post by cascade9 on 2010-01-10
Been running 64bit for a while now, and I'm yet to find anything that wont work on 64bit. 

Go on, use 64bit, enjoy the extra number crunching powa!!! it gives you :D

---

### Post by dcstar on 2010-01-11
> **Mia_tech said:**
> yes, I was aware of OS 32=4G and 64=128G, but the thing that threw me off was the **rare number reported by the OS, which is 3.2**. Now, one of the draw back of 64 is the lack of support of drivers and applications...

You need to understand the difference between GiB and GB, and what your BIOS steals.

---

### Post by tad1073 on 2010-01-11
> **lotharmat said:**
> Ubuntu 32 bit will only ever report 3.2 gig evAr

a pae kernel, which is for 32 bit os's,  addresses all available memory. I used a 32 bit ubuntu os, put a pae kernel in and 5.9gb' s of memory was addresses, with the 64 bit, 5.8gb's was addressed.

---

### Post by NoaHall on 2010-01-11
> **tad1073 said:**
> a pae kernel, which is for 32 bit os's,  addresses all available memory. I used a 32 bit ubuntu os, put a pae kernel in and 5.9gb' s of memory was addresses, with the 64 bit, 5.8gb's was addressed.

PAE kernels make the system into 36 bit.

---

