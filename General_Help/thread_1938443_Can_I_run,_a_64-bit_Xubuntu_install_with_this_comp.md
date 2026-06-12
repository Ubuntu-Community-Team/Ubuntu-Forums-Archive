---
title: "Can I run, a 64-bit Xubuntu install with this computer?"
date: 2012-03-09
forum: General Help
---

### Post by mikodo on 2012-03-09
Hi,

Can I run, a 64-bit Xubuntu install with this computer, (always used 32-bit before)?

```
sudo lshw
``````
*-cpu:0
          description: CPU
          product: Intel(R) Core(TM)2 Quad CPU    Q6600  @ 2.40GHz
          vendor: Intel Corp.
          physical id: 4
          bus info: cpu@0
          version: 6.15.11
          serial: 0000-06FB-0000-0000-0000-0000
          slot: CPU 1
          size: 1596MHz
          capacity: 2400MHz
        **  width: 64 bits**
          clock: 267MHz
```This cpu will handle up to 8 gigs of ram. I intend to install it, if I am told here, I can use 64-bit processing.

Thanks.

---

### Post by forrestcupp on 2012-03-09
Yes, I would say you could. I'd run the LiveCD and just see if it works. If I recall correctly, you can't upgrade from 32-bit to 64-bit, anyway. So you'll have to do a clean install. I'm sure it will work, though, especially if 32-bit worked.

---

### Post by mikodo on 2012-03-09
> **forrestcupp said:**
> Yes, I would say you could. I'd run the LiveCD and just see if it works. If I recall correctly, you can't upgrade from 32-bit to 64-bit, anyway. So you'll have to do a clean install. I'm sure it will work, though, especially if 32-bit worked.
Thank you.

It will be a clean install.

I never thought of using the live CD to try it out. Duh!

Thanks.

---

### Post by collisionystm on 2012-03-09
Yes. Yes you can.

---

### Post by mikodo on 2012-03-09
> **collisionystm said:**
> Yes. Yes you can.
Thanks.

---

### Post by mikodo on 2012-03-09
Yes, the Xubuntu 12.04 AMD64 - LiveCD, is working like a charm for me. Once, I get to know my way around Xubuntu 12.10, after installing it towards EOL of Ubuntu 10.04, I am really going to like it. Probably, more than Gnome2! Even on the LiveCD, it is really snappy! 

For inversion, this works great! So, no more CCSM, for me.

```
xcalib -invert -alter
```

I am finding a few bugs, in Abiword -> one is where my center mouse button doesn't seem to work,(will not scroll), and I am getting signaled to report crashes, within it. 

Other than that, for now, everything is working, Tickity-Boo! (don't know if that is a word; one of my daughters' nick ... She doesn't like me to use it anymore, now that she is grown).

:D

---

### Post by &#1048;&#1075;&#1086;&#1088; on 2012-03-09
How much you have memory (RAM)?
If you are not advanced user (you don know how to handle x86 programs in x64 system) it is not recomended to run x64 system with less than 4 GB RAM.
Sorry for my english....

---

### Post by grahammechanical on 2012-03-09
Pardon me!

I only have 1GB of RAM and I am running Ubuntu 64bit on my Intel core 2 @ 2.4Ghz. I am actually running 12.04 Beta 1 and System Info (now called Details) is clear that I have a 64bit OS.

Regards.

---

### Post by mikodo on 2012-03-09
> **&#1048 said:**
> How much you have memory (RAM)?
If you are not advanced user (you don know how to handle x86 programs in x64 system) it is not recomended to run x64 system with less than 4 GB RAM.
Sorry for my english....
Oh hi,

Well, I do have 4 gigs of ram now. Before, I clean install Xubuntu 12.10, with the AMD 64-bit installer, I plan to add, 4 more gigs of RAM.

Thanks.

---

### Post by forrestcupp on 2012-03-10
> **&#1048 said:**
> How much you have memory (RAM)?
If you are not advanced user (you don know how to handle x86 programs in x64 system) it is not recomended to run x64 system with less than 4 GB RAM.
Sorry for my english....

Yeah, that's definitely not true, unless maybe you only have like 512MB. Also, it was true at one time that you had to put a little effort into running 32-bit apps in 64-bit Ubuntu, but they have done things more recently to take the pain out of it.

---

