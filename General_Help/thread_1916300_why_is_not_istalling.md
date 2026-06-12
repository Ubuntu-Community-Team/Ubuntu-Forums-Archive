---
title: "why is not istalling?"
date: 2012-01-27
forum: General Help
---

### Post by nataliafoster26 on 2012-01-27
im using virtual box to install ubuntu 10.4 64bit. and i keep getting this message

this kernel requires an x86-64 cpu,but only detected an i686 cpu. 
ubable to boot- please use a kernel appropriate for your cpu

not sure what it means i got windows 7 , 64bit

and is also not the first time i have try

---

### Post by 3rdalbum on 2012-01-27
> **nataliafoster26 said:**
> im using virtual box to install ubuntu 10.4 64bit. and i keep getting this message

this kernel requires an x86-64 cpu,but only detected an i686 cpu. 
ubable to boot- please use a kernel appropriate for your cpu

not sure what it means i got windows 7 , 64bit

and is also not the first time i have try

Virtualbox emulates a 32-bit CPU by default. There are options in the virtual machine settings to enable 64-bit guest OSes if your CPU supports the correct functions. I can't remember what those settings are labelled, but you can look at the tooltips for each setting and it will tell you.

If those settings are greyed-out and can't be clicked, then you are limited to using a 32-bit guest OS. However you can still run 64-bit Ubuntu directly on your hardware by booting the CD.

---

### Post by nataliafoster26 on 2012-01-27
ok couldnt figure out how to change so im just going to get 32 bit

---

