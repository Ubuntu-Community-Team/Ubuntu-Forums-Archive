---
title: "Whither 64 bits (ARGH!)"
date: 2012-05-13
forum: General Help
---

### Post by M_Mynaardt on 2012-05-13
Hi there!

I just stumbled on some information about finding out if one's computer is, in fact a 64 bit machine.  I just assumed that my computers were 32 bit, as they're not brand spanking new.  But it looks like the desktop, at least, is a 64 bit machine.  I typed this in, per the bit I stumbled upon:

```
:~$ grep --color=always -iw lm /proc/cpuinfo
flags		: fpu vme de pse tsc msr pae mce cx8 apic mtrr pge mca cmov pat pse36 clflush mmx fxsr sse sse2 ht syscall nx mmxext fxsr_opt [COLOR="Red"]**lm**[/COLOR] 3dnowext 3dnow pni lahf_lm cmp_legacy
flags		: fpu vme de pse tsc msr pae mce cx8 apic mtrr pge mca cmov pat pse36 clflush mmx fxsr sse sse2 ht syscall nx mmxext fxsr_opt [COLOR="red"]**lm**[/COLOR] 3dnowext 3dnow pni lahf_lm cmp_legacy

```

I saw that there are a couple of "lm" flags that appear in this output.  Just to be absolutely sure; that does mean the computer I did this on is a 64 bit machine, doesn't it?

If so, I guess I really should install the 64 bit version of Xubuntu.  This could go a long way to explaining why Precise Pangolin has been a bit temperamental, if I'm running the 32 bit version on a 64 bit machine...
#-o

Thanks!

---

### Post by jadtech on 2012-05-13
some computer  lap tops for sure  are  dual core one  core deactivated for  speed and power control, battery life  what ever i questioned a while  they label them as 64bit supported .. better  way to know is if  you computer suport more then 3 gb of ram this is mainly the difference  between 32 and 64  how much memmory it can address 32 bit cant address more then 3 gb of ram ..

---

### Post by flemur13013 on 2012-05-13
32 bit CAN access more then 3 GB (or 4GB) of memory with PAE, which is (or was) the default for ubuntu kernels.

FWIW, I get **lm** and **dtes64** output from "grep --color=always -iw lm /proc/cpuinfo" on 64 bit machine w/64 bit OS.

---

### Post by rai4shu2 on 2012-05-13
Another good way to check is:

```
lscpu | grep mode
```

---

### Post by idoitprone on 2012-05-13
Amd 64 can support both 32 bit and 64 bit machines

x86 architecture is some complex instruction set

There is a diffference between 32 and 64 bit processors and operating system

In linux it simple to check for both

cat /proc/cpuinfo to dump cpu info to check if 64 or 32 bit processor

[https://help.ubuntu.com/community/32bit_and_64bit](https://help.ubuntu.com/community/32bit_and_64bit)

uname -p check if the so is 64 bit

If uname returns x86_64 then it is 64 bit os
is it returns i6XX or i3XX or any other i then it is a 32 bit os

---

