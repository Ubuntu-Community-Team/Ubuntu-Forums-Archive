---
title: "virtualbox is always 32 bit emulation?"
date: 2010-04-18
forum: General Help
---

### Post by muteXe on 2010-04-18
Hiya,
Dowloaded 10.04 beta 2 64 bit iso and was trying to install it into a VM. Upon boot however is comes up with something like "cant install it on your 32bit machine".
I'm fairly sure my laptop has a 64 bit architecture (for example, i have the "lm" flag when i cat the /proc/cpuinfo), so is there a way to convince VB that I have a 64 bit machine?  unless there is a better way to find out if my CPU is indeed NOT 64 bit?

Many thanks,

Tom

---

### Post by howefield on 2010-04-18
Have you enabled VT-x/AMD-V in your Vm settings, if you have perhaps your processor doesn't support it.

What is the make/model of your processor ?

---

### Post by muteXe on 2010-04-18
It appears i do have that checkbox ticked in VB.

cat /proc/cpuinfo:

```

processor	: 0
vendor_id	: GenuineIntel
cpu family	: 6
model		: 15
model name	: Intel(R) Core(TM)2 Duo CPU     T5550  @ 1.83GHz
stepping	: 13
cpu MHz		: 1000.000
cache size	: 2048 KB
physical id	: 0
siblings	: 2
core id		: 0
cpu cores	: 2
fdiv_bug	: no
hlt_bug		: no
f00f_bug	: no
coma_bug	: no
fpu		: yes
fpu_exception	: yes
cpuid level	: 10
wp		: yes
flags		: fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe nx lm constant_tsc arch_perfmon pebs bts pni monitor ds_cpl est tm2 ssse3 cx16 xtpr lahf_lm
bogomips	: 3657.60
clflush size	: 64

processor	: 1
vendor_id	: GenuineIntel
cpu family	: 6
model		: 15
model name	: Intel(R) Core(TM)2 Duo CPU     T5550  @ 1.83GHz
stepping	: 13
cpu MHz		: 1000.000
cache size	: 2048 KB
physical id	: 0
siblings	: 2
core id		: 1
cpu cores	: 2
fdiv_bug	: no
hlt_bug		: no
f00f_bug	: no
coma_bug	: no
fpu		: yes
fpu_exception	: yes
cpuid level	: 10
wp		: yes
flags		: fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe nx lm constant_tsc arch_perfmon pebs bts pni monitor ds_cpl est tm2 ssse3 cx16 xtpr lahf_lm
bogomips	: 3657.50
clflush size	: 64


```

Many thanks in advance,
Tom

---

### Post by blueridgedog on 2010-04-18
Are you running a 64 bit OS?  What is the output of 

```
uname -a
```

---

### Post by huygens on 2010-04-18
The problem you have is that your host Linux operating system is most probably 32bit, so when using VirtualBox you can virtualise only other 32bit systems, unless your processor supports virtualisation instructions (called VT-x/AMD-V).
So if you have a processor that supports 64bit instructions and as the VT-x/AMD-V support, even though you have a 32bit host, you can run 64bit guests.

Now, Intel Core2 Duo should support both sets of instructions (64bit and virtualisation) however, seeing your flags, it does not show up. You should have the vmx/svm flags on to be able to virtualise a 64bit system. The main reason for this is: your laptop/desktop manufacturer probably disabled those instructions set in the BIOS.

Solution : reboot your computer, go to the BIOS, and look for advanced CPU features. Activate virutalisation VT-X/AMD-V feature. Boot to Linux, and now you should be able to virtualise 64bit guest.

---

### Post by theozzlives on 2010-04-18
+1 on the BIOS!

---

### Post by howefield on 2010-04-18
Appears that your processor is incapable of running 64 bit virtual machines in a 32 bit host, (although it can run a 64 bit host).

[http://ark.intel.com/Product.aspx?id=32427&processor=T5550&spec-codes=SLA4E](http://ark.intel.com/Product.aspx?id=32427&processor=T5550&spec-codes=SLA4E)

---

### Post by huygens on 2010-04-18
Howefield is right. **** I thought every Core2Duo supported VT-x instructions.
For the price you pay Intel hardware, sometimes I do not get their politics...

---

### Post by muteXe on 2010-04-18
My host is indeed 32bit, ubuntu 8.04.

Many thanks for all the help. I've just gone and got the 32bit lucid to see what it's like in VB.  If I like, i'll install the 64 bit version on my laptop.
First though i'm gonna check out the BIOS setting.

Brb :)

Thanks again,

Tom

---

### Post by muteXe on 2010-04-18
Well i cant find any advanced options in my bios about the CPU. In fact all of the CPU data i can see is read-only.

I'm gonna install 32bit in VB I think.

Thanks again,

Tom

---

### Post by howefield on 2010-04-18
> **muteXe said:**
> Well i cant find any advanced options in my bios about the CPU.

If the processor isn't capable, then no amount of BIOS settings will change that and make it capable. ;)

---

