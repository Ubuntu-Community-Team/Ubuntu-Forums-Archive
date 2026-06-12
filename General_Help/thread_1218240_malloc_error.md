---
title: "malloc error"
date: 2009-07-20
forum: General Help
---

### Post by CallahanOSU on 2009-07-20
I'm attempting to run hmmalign from HMMer 2.3.2 on Hardy Heron LTS. I've tried three attempts with the same input file and they all return the same error message.

> FATAL: malloc of 54705 bytes failed: file msa.c line 80I'm trying to make sure I have the correct interpretation of this error message -- the system is failing to allocate free memory to run line 80 of this protocol, msa.c, and so my attempt to run hmmalign ends. Does a message like this mean the problem is with malloc itself or with the file that is trying to run? Does it simply mean that the memory is not there to allocate? Can somebody tell me if msa.c is a system file or something specific to HMMer? And is there something I can do to diagnose my system's ability for free memory allocation?

Any help offered is greatly appreciated. Thank you.

---

