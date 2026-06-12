---
title: "how check my laptop for 32bit or 64bit"
date: 2009-12-09
forum: General Help
---

### Post by kasrawis on 2009-12-09
i typed in internimal uname -a i get the following

naseer@naseer-laptop:~$ uname -a
Linux naseer-laptop 2.6.31-14-generic #48-Ubuntu SMP Fri Oct 16 14:04:26 UTC 2009 i686 GNU/Linux



so how do i know is it 32bit or 64 

thanks i already search everywhere couldn't find exact why

---

### Post by prem1er on 2009-12-09
Are you trying to find out if your cpu is 64 bit or if your ubuntu installation is 64 bit?

---

### Post by soni1770 on 2009-12-09
your running a 32bit OS

but your computer may still be 64 bit

try

**cat /proc/cpuinfo**

in the ternimal

post the output

---

### Post by krimzonstarr on 2009-12-09
Not the OP, but I am interested since I can't find out specifically if the Intel Atom is 32-bit or 64-bit. Here is my /proc/cpuinfo...

> krimzonstarr@krimzubuaa1:~$ cat /proc/cpuinfo
processor	: 0
vendor_id	: GenuineIntel
cpu family	: 6
model		: 28
model name	: Intel(R) Atom(TM) CPU N270   @ 1.60GHz
stepping	: 2
cpu MHz		: 1600.000
cache size	: 512 KB
physical id	: 0
siblings	: 2
core id		: 0
cpu cores	: 1
apicid		: 0
initial apicid	: 0
fdiv_bug	: no
hlt_bug		: no
f00f_bug	: no
coma_bug	: no
fpu		: yes
fpu_exception	: yes
cpuid level	: 10
wp		: yes
flags		: fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe constant_tsc arch_perfmon pebs bts aperfmperf pni dtes64 monitor ds_cpl est tm2 ssse3 xtpr pdcm movbe lahf_lm
bogomips	: 3191.59
clflush size	: 64
cache_alignment	: 64
address sizes	: 32 bits physical, 32 bits virtual
power management:

processor	: 1
vendor_id	: GenuineIntel
cpu family	: 6
model		: 28
model name	: Intel(R) Atom(TM) CPU N270   @ 1.60GHz
stepping	: 2
cpu MHz		: 1600.000
cache size	: 512 KB
physical id	: 0
siblings	: 2
core id		: 0
cpu cores	: 1
apicid		: 1
initial apicid	: 1
fdiv_bug	: no
hlt_bug		: no
f00f_bug	: no
coma_bug	: no
fpu		: yes
fpu_exception	: yes
cpuid level	: 10
wp		: yes
flags		: fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe constant_tsc arch_perfmon pebs bts aperfmperf pni dtes64 monitor ds_cpl est tm2 ssse3 xtpr pdcm movbe lahf_lm
bogomips	: 3191.95
clflush size	: 64
cache_alignment	: 64
address sizes	: 32 bits physical, 32 bits virtual
power management:


EDIT: Ok, after getting that output, I was able to track it down using the model number. The Intel Atom N270 does not support 64-bit, but is hyperthreaded I guess. Oh well.

---

### Post by kasrawis on 2009-12-09
processor	: 0
vendor_id	: GenuineIntel
cpu family	: 6
model		: 14
model name	: Intel(R) Celeron(R) M CPU        420  @ 1.60GHz
stepping	: 8
cpu MHz		: 1600.033
cache size	: 1024 KB
fdiv_bug	: no
hlt_bug		: no
f00f_bug	: no
coma_bug	: no
fpu		: yes
fpu_exception	: yes
cpuid level	: 10
wp		: yes
flags		: fpu vme de pse tsc msr pae mce cx8 apic mtrr pge mca cmov clflush dts acpi mmx fxsr sse sse2 ss tm pbe constant_tsc up arch_perfmon bts pni monitor tm2 xtpr pdcm
bogomips	: 3200.06
clflush size	: 64
power management:

here it is please tell me is it 64bit i think it is

---

### Post by soni1770 on 2009-12-09
krimzonstarr 

it's looks like you've got a 32 bit setup.








[http://ark.intel.com/Compare.aspx?ids=35635,35641,36331,35472,35469,41175,41176,40740,35466,41174,35463,41173,35460,40741](http://ark.intel.com/Compare.aspx?ids=35635,35641,36331,35472,35469,41175,41176,40740,35466,41174,35463,41173,35460,40741),

---

### Post by kasrawis on 2009-12-09
> **soni1770 said:**
> krimzonstarr 

it's looks like you've got a 32 bit setup.








[http://ark.intel.com/Compare.aspx?ids=35635,35641,36331,35472,35469,41175,41176,40740,35466,41174,35463,41173,35460,40741](http://ark.intel.com/Compare.aspx?ids=35635,35641,36331,35472,35469,41175,41176,40740,35466,41174,35463,41173,35460,40741),

yes i know i've install 32bit ubuntu but only wanna know if my laptop is 64bit supported or no 
thanks for reply

---

### Post by soni1770 on 2009-12-09
kasrawis


**Intel® Celeron® M Processor 420 (1M Cache, 1.60 GHz, 533 MHz FSB**



also looks 32 bit setup....


[http://ark.intel.com/Product.aspx?id=27149](http://ark.intel.com/Product.aspx?id=27149)

---

### Post by kasrawis on 2009-12-09
ok thank you i got it this is 32bit machine wanted to install ubuntu server edition in this can i ?

---

### Post by soni1770 on 2009-12-09
yip, as long as you download the 32bit version



[http://www.ubuntu.com/getubuntu/download-server](http://www.ubuntu.com/getubuntu/download-server)


choose [B][Alternative download options]("http://www.ubuntu.com/getubuntu/download-server#")

select 32bit
[/B]

---

### Post by firsttimeuser on 2009-12-09
actually when you run "uname -a", if you don't see X86_64, your system is 32bit.

@dao:~$ uname -a
Linux dao 2.6.28-11-server #42-Ubuntu SMP Fri Apr 17 02:45:36 UTC 2009 x86_64 GNU/Linux

---

