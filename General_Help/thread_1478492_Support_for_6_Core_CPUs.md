---
title: "Support for 6 Core CPUs"
date: 2010-05-09
forum: General Help
---

### Post by pAsM on 2010-05-09
Greetings All,
[INDENT]
I have just purchased an AMD Phenom II 1055T 6 Core CPU to replace my aging CPU. The problem is only 1 core is visible to Ubuntu, Does it actually support 6 cores? 
[/INDENT]

---

### Post by TheForkOfJustice on 2010-05-09
Good question.

Anyone know if it even treats quad cores (like mine) well?

Anyone know of any benchmarks?

---

### Post by pAsM on 2010-05-09
> **TheForkOfJustice said:**
> Good question.

Anyone know if it even treats quad cores (like mine) well?

Anyone know of any benchmarks?


I would be happy to do a benchmark if I can get everything working :)

---

### Post by WorMzy on 2010-05-09
I've seen one guy post who said he had 24 cores. I don't know how legitimate that was, but I can confirm that my dual core is supported, and I've seen quad-cores work fine, so I have to assume that quincore and sexcore processors are also supported. Where are you seeing only one core?

---

### Post by pAsM on 2010-05-09
> **WorMzy said:**
> I've seen one guy post who said he had 24 cores. I don't know how legitimate that was, but I can confirm that my dual core is supported, and I've seen quad-cores work fine, so I have to assume that quincore and sexcore processors are also supported. Where are you seeing only one core?
Greetings,
[INDENT]I see this on the Gnome System Monitor and even by running a cat /proc/cpuinfo (Output below)

processor    : 0
vendor_id    : AuthenticAMD
cpu family    : 16
model        : 10
model name    : Dual-Core AMD Opteron(tm) Processor 130500 Dual-
stepping    : 0
cpu MHz        : 878.380
cache size    : 512 KB
physical id    : 0
siblings    : 1
core id        : 0
cpu cores    : 1
apicid        : 0
initial apicid    : 0
fpu        : yes
fpu_exception    : yes
cpuid level    : 6
wp        : yes
flags        : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush mmx fxsr sse sse2 ht syscall nx mmxext fxsr_opt pdpe1gb rdtscp lm 3dnowext 3dnow constant_tsc up rep_good nonstop_tsc extd_apicid pni monitor cx16 popcnt lahf_lm cmp_legacy svm extapic cr8_legacy abm sse4a misalignsse 3dnowprefetch osvw ibs skinit wdt
bogomips    : 1756.75
TLB size    : 1024 4K pages
clflush size    : 64
cache_alignment    : 64
address sizes    : 48 bits physical, 48 bits virtual
power management: ts ttp tm stc 100mhzsteps hwpstate [9]


I also did a lshw and the output is [https://k-disk.net/lshw.txt](https://k-disk.net/lshw.txt)
[/INDENT]

---

### Post by happyhamster on 2010-05-09
Are you sure the motherboard supports the processor? I ask because it's not in this list (yet):
[http://www.msi.com/index.php?func=prodcpu2&prod_no=1863&maincat_no=1](http://www.msi.com/index.php?func=prodcpu2&prod_no=1863&maincat_no=1)
(You'll likely have to update the bios.)

For proof that the processor works with ubuntu:
[http://www.linux-magazine.com/Online/News/Phenom-II-X6-Performance-Under-Linux-Below-Expectations](http://www.linux-magazine.com/Online/News/Phenom-II-X6-Performance-Under-Linux-Below-Expectations)

---

### Post by pAsM on 2010-05-12
Hello All,
[INDENT]I got a new motherboard and BAM it works perfectly. This machine is a monster. Here is a benchmark.I have also added a few screenshots as well. Enjoy


**Benchmarks**

CPU Blowfish CPU Blowfish   **This Machine**1500  MHz3.012   Intel(R) Celeron(R) M processor         1.50GHz(null)26.1876862   PowerPC 740/750 (280.00MHz)(null)172.816713 CPU  CryptoHash CPU CryptoHash   **This Machine**1500  MHz514.469 CPU  Fibonacci CPU Fibonacci   **This Machine**1500  MHz3.469   Intel(R) Celeron(R) M processor         1.50GHz(null)8.1375674   PowerPC 740/750 (280.00MHz)(null)58.07682 CPU  N-Queens CPU N-Queens   **This Machine**1500  MHz0.932 FPU FFT FPU FFT   **This Machine**1500  MHz2.017 FPU  Raytracing FPU Raytracing   **This Machine**1500  MHz14.470   Intel(R) Celeron(R) M processor         1.50GHz(null)40.8816714   PowerPC 740/750 (280.00MHz)(null)161.312647
[/INDENT]

---

### Post by izz.y on 2010-05-20
The motherboard was incompatible with the processor. According to the lshw, You have an MSI K9N6PGM2-V2. According to MSI's website, the K9N6PGM2-V2 only supports 95W processors, and you were using an AMD 1045T which is 125W. The motherboard or processor must have has some sort of feature which disables all but 1 core so the computer would be usable. I am not trying to sound harsh, but it is important to check and make sure that your motherboard and processor are 100% compatible, before even installing the processor, because it could cause severe damage to your system. I am glad to here that you got it working though.

---

