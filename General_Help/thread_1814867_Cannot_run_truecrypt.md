---
title: "Cannot run truecrypt"
date: 2011-07-30
forum: General Help
---

### Post by Plitvix on 2011-07-30
Hello,
I have downloaded Truecrypt from [http://www.truecrypt.org/downloads](http://www.truecrypt.org/downloads) (32 bit standard, newest version). 
Extracted and run setup, clicked on install  - I didn't extract it to /tmp, but installed right away. All went fine. No errors. 
Then I tried to open it from Applications -> Accessories -> Truecrypt. Didn't work. 
```
sudo /usr/bin/truecrypt
``` returns this error:
> truecrypt: error while loading shared libraries: libfuse.so.2: wrong ELF class: ELFCLASS64

Here is some details on my laptop:
Linux ubuntu 2.6.38-8-generic #42-Ubuntu SMP Mon Apr 11 03:31:24 UTC 2011 x86_64 x86_64 x86_64 GNU/Linux

Installed using Wubi. My system is 32 bit. 
Processor: Intel(R) Pentium(R) Dual  CPU  T2390  @ 1.86GHz - 2 cores
RAM: 2 GB.
GPU: nVidia 9400 mobile - I didn't install any additional drivers but those provided by Ubuntu itself. 


Thanks in advance!

---

### Post by whitethorn on 2011-07-30
> **Plitvix said:**
> Hello,
I have downloaded Truecrypt from (32 bit standard, newest version). 

Here is some details on my laptop:
Linux ubuntu 2.6.38-8-generic #42-Ubuntu SMP Mon Apr 11 03:31:24 UTC 2011 x86_64 x86_64 x86_64 GNU/Linux

Installed using Wubi. My system is 32 bit. 
Thanks in advance!

Ehh this seems kinda contradictory, firstly what your running is a 64-bit OS. x86_64 == 64-bit. The failure your getting is a missing library.

I'm guessing you should try downloading the x64 version of truecrypt and try the install again.

Just to clarify things could you also post the output of

```
uname -a
```

---

### Post by Plitvix on 2011-07-30
LOL
I have 32 bit hardware. And Wubi downloaded 64 bit version of Ubuntu. Now that is a problem. 


Actually, I am not sure if my hardware is 32 bits. My Windows was 32 bits for sure and worked fine.


I am kind of feeling stupid right now.
Uname -a is in first post.
Well, thanks. Installed 64 bit version, everything is working fine. 

-.-

---

