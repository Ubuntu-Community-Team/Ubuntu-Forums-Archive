---
title: "Know your processor !!!"
date: 2012-07-31
forum: General Help
---

### Post by ramakanta on 2012-07-31
How to know it is 32bit computeror (32bit processor)and it is 64 bit computeror( 64 bit processor)?? Is there any procedure to know it ??? Please help me .
 thank you.
 
:confused::confused:

---

### Post by mastablasta on 2012-07-31
have a look here: [http://en.wikipedia.org/wiki/64-bit](http://en.wikipedia.org/wiki/64-bit)

---

### Post by Statia on 2012-07-31
In a terminal, type the command:

cat /proc/cpuinfo

It will output info about your CPU('s).
Then you can google the model.

[edit]

Or skip the googly bit altogether and log for the string 'lm' in the section "flags".

---

### Post by levlaz on 2012-07-31
If you open a terminal and type 

```
uname -m
```

It will tell you what type of processor you have. 

For example on my macbook Pro I typed it and it says "x86_64" this means I have a 64 bit processor.

---

### Post by nmaster on 2012-07-31
> **levlaz said:**
> If you open a terminal and type 

```
uname -m
```It will tell you what type of processor you have. 

For example on my macbook Pro I typed it and it says "x86_64" this means I have a 64 bit processor.
this is not completely true.  it says "x86_64" because you are using a 64-bit OS.  however, you can install a 32-bit OS if your processor is x64.  for example, "uname -m" gives me "i686" because i installed a 32-bit OS even though i have a 64-bit processor.

another way to find out information on your processor is with lshw.


```

neal@neal-DEV-Ubuntu:/home/neal 
$ sudo lshw -C cpu
[sudo] password for neal: 
  *-cpu                   
       description: CPU
       product: Intel(R) Core(TM) i5-2520M CPU @ 2.50GHz
       vendor: Intel Corp.
       physical id: 1
       bus info: cpu@0
       version: 6.10.7
       serial: 0002-06A7-0000-0000-0000-0000
       slot: CPU
       size: 800MHz
       capacity: 800MHz
       width: 64 bits
       clock: 100MHz
       capabilities: x86-64 fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe nx rdtscp constant_tsc arch_perfmon pebs bts xtopology nonstop_tsc aperfmperf pni pclmulqdq dtes64 monitor ds_cpl vmx smx est tm2 ssse3 cx16 xtpr pdcm pcid sse4_1 sse4_2 x2apic popcnt tsc_deadline_timer aes xsave avx lahf_lm ida arat epb xsaveopt pln pts tpr_shadow vnmi flexpriority ept vpid cpufreq
       configuration: cores=2 enabledcores=2 id=1 threads=4
     *-logicalcpu:0
          description: Logical CPU
          physical id: 1.1
          width: 64 bits
          capabilities: logical
     *-logicalcpu:1
          description: Logical CPU
          physical id: 1.2
          width: 64 bits
          capabilities: logical
     *-logicalcpu:2
          description: Logical CPU
          physical id: 1.3
          width: 64 bits
          capabilities: logical
     *-logicalcpu:3
          description: Logical CPU
          physical id: 1.4
          width: 64 bits
          capabilities: logical
     *-logicalcpu:4
          description: Logical CPU
          physical id: 1.5
          width: 64 bits
          capabilities: logical
     *-logicalcpu:5
          description: Logical CPU
          physical id: 1.6
          width: 64 bits
          capabilities: logical
     *-logicalcpu:6
          description: Logical CPU
          physical id: 1.7
          width: 64 bits
          capabilities: logical
     *-logicalcpu:7
          description: Logical CPU
          physical id: 1.8
          width: 64 bits
          capabilities: logical
     *-logicalcpu:8
          description: Logical CPU
          physical id: 1.9
          width: 64 bits
          capabilities: logical
     *-logicalcpu:9
          description: Logical CPU
          physical id: 1.a
          width: 64 bits
          capabilities: logical
     *-logicalcpu:10
          description: Logical CPU
          physical id: 1.b
          width: 64 bits
          capabilities: logical
     *-logicalcpu:11
          description: Logical CPU
          physical id: 1.c
          width: 64 bits
          capabilities: logical
     *-logicalcpu:12
          description: Logical CPU
          physical id: 1.d
          width: 64 bits
          capabilities: logical
     *-logicalcpu:13
          description: Logical CPU
          physical id: 1.e
          width: 64 bits
          capabilities: logical
     *-logicalcpu:14
          description: Logical CPU
          physical id: 1.f
          width: 64 bits
          capabilities: logical
     *-logicalcpu:15
          description: Logical CPU
          physical id: 1.10
          width: 64 bits
          capabilities: logical
neal@neal-DEV-Ubuntu:/home/neal 
$ uname -m
i686

```

---

