---
title: "RAM recognize full memory"
date: 2010-06-25
forum: General Help
---

### Post by dragos2 on 2010-06-25
I replaced dual memory kit DDR2 from 2 GB kit to 4 GB kit and the system boots but
it recognizes only 3 GB ..

Any idea ?

```

dragos@lucid:~$ cat /proc/meminfo
MemTotal:        3089344 kB
MemFree:         2829664 kB
Buffers:           12032 kB
Cached:            58932 kB
SwapCached:            0 kB
Active:            86984 kB
Inactive:          48388 kB
..

```and
```

dragos@lucid:~$ free -m
             total       used       free     shared    buffers     cached
Mem:          3016        236       2780          0         11         57
-/+ buffers/cache:        166       2850
Swap:         5135          0       5135

```

---

### Post by Sub101 on 2010-06-25
What version of Ubuntu are you using?

If it is the 32-bit you can not see more than 3Gb of ram.

---

### Post by burton247 on 2010-06-25
Firstly a post basically the same as this was answered about half an hour ago. And secondly a 32bit OS can address 4GB of memory. But this is all the memory on your computer not just "RAM" (technically your hard drive is RAM)

---

### Post by Sub101 on 2010-06-25
> **burton247 said:**
>  And secondly a 32bit OS can address 4GB of memory. But this is all the memory on your computer not just "RAM" (technically your hard drive is RAM)

Really...? 

For the OP you can only see 3Gb on 32bit. You can see as much as you want with 64bit.

---

### Post by burton247 on 2010-06-25
The address bus is 32 bits wide so it can address 2^32 memory locations, which is quite a lot to write out but it's just 4GB (of locations) But it's got to do all the memory, like on your graphics card, depending on the processor and how the I/O is mapped it may have separate section for that (or it might just be part of your "RAM")

And finally, if I've done my maths correctly you can address 16777216 terrabytes of memory on a 64 bit OS. so why they are bothering with 128bit OS's is beyond me!

I wrote all that out and now I'm wondering what your really was in response to haha

---

### Post by dragos2 on 2010-06-25
Its a UEC node, Lucid 64 bit

```

dragos@luvid:~$ lsb_release -a
No LSB modules are available.
Distributor ID: Ubuntu
Description:    Ubuntu 10.04 LTS
Release:        10.04
Codename:       lucid

```

```

dragos@lucid:~$ uname -a
Linux node1 2.6.32-22-server #36-Ubuntu SMP Thu Jun 3 20:38:33 UTC 2010 x86_64 GNU/Linux

```In BIOS I can see it recognizes 4096 MB with 256 MB Shared.

---

### Post by warfacegod on 2010-06-25
A 32 bit OS (even Windows) can "see" more than 3 GB of RAM and with Linux with a PAE kernel you can even use it. I don't suggest this option because you can take a performance hit even with the additional RAM.

Do this: Go to Applications> Accessories> Terminal

```
sudo lshw
```

Scroll back to the top of the display and look for *cpu. It will look something like this:

```
*-cpu
          description: CPU
          product: Intel(R) Pentium(R) 4 CPU 2.80GHz
          vendor: Intel Corp.
          physical id: 4
          bus info: cpu@0
          version: 15.2.9
          slot: NWD
          size: 2800MHz
          capacity: 3200MHz
          width: 32 bits

```

You'll notice on the bottom it says "width: 32 bits" on  mine. Means my processor is 32 bit. If yours says 64 then you can use a 64 bit OS which is what you should do if you want to use that new RAM to its fullest potential. If you have 32 bit, you'll have no other options but using the PAE kernel or leave well enough alone and be satisfied with 3.3 GB RAM.

---

### Post by burton247 on 2010-06-25
How odd...You could search for any known issues with your ram and linux/the specific distro. The BIOS can usually detect everything fine. But once the OS kicks in the BIOS doesn't handle it anymore. There's often issues the people not being able to use all their hard drives. Thats because you need specific drivers to be able to use it all. I haven't heard of this with RAM before but you may want to check it out

---

### Post by philinux on 2010-06-25
Already had this today. lol

[http://ubuntuforums.org/showthread.php?t=1517482](http://ubuntuforums.org/showthread.php?t=1517482)

---

### Post by burton247 on 2010-06-25
> **warfacegod said:**
> 
You'll notice on the bottom it says "width: 32 bits" on  mine. Means my processor is 32 bit. If yours says 64 then you can use a 64 bit OS which is what you should do if you want to use that new RAM to its fullest potential. If you have 32 bit, you'll have no other options but using the PAE kernel or leave well enough alone and be satisfied with 3.3 GB RAM.

Can you still install the 64bit version on a 32bit CPU?

Even so, theres 4 gig system mem, 256 gpu mem. The rest doesn't take up much space. There should be about 3.5gb of addressable system memory but there's currently less than 3 :S


> **philinux said:**
> Already had this today. lol

[http://ubuntuforums.org/showthread.php?t=1517482](http://ubuntuforums.org/showthread.php?t=1517482)

I thought that at first but it is different this time

---

### Post by warfacegod on 2010-06-25
> Can you still install the 64bit version on a 32bit CPU?

No.

You can do 32 onto 64 but not the other way around.

---

### Post by burton247 on 2010-06-25
That's what I thought. The OP said he has a 64bit Lucid installed ;)

---

### Post by warfacegod on 2010-06-25
He edited that post after I'd already posted. I didn't see it until it was too late. Stating in post #1 that Lucid 64 was in use would have saved time and confusion.

---

### Post by dragos2 on 2010-06-25
Its a 64 bit CPU

```

     *-cpu
          ...
          width: 64 bits
          capabilities: fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36

```
   
I also booted with Live CD Knoppix which showed 3.3 GB, so that is probably PAE, but
this is a UEC node installed with Lucid.

---

