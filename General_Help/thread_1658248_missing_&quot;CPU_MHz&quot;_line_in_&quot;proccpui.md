---
title: "missing &quot;CPU MHz&quot; line in &quot;/proc/cpuinfo&quot;"
date: 2011-01-02
forum: General Help
---

### Post by buntuyu on 2011-01-02
I don't have a "CPU MHz" line in my /proc/cpuinfo

I wonder if this is because I installed a 32-bit Ubuntu (10.10, Maverick) on 64-bit (dual core) AMD hardware.

Various apps depend on the "CPU MHz" value and simply refuse to run without it.

Is it, indeed, a 32-bit software on 64-bit hardware thing? If so, is there any fix short of replacing (clean-installing) the whole system in 64-bit ?  Perhaps it's not the latter? Does anyone else have this problem? (either with 64-bit or 32-bit software)

Thanks in advance!

$ uname -a:

..... 2.6.32-27-generic #49-Ubuntu SMP Wed Dec 1 23:52:12 UTC 2010 i686 GNU/Linux

$ cat /proc/cpuinfo:

processor	: 0
vendor_id	: AuthenticAMD
cpu family	: 15
model		: 104
model name	: AMD Turion(tm) 64 X2 Mobile Technology TL-58
stepping	: 1
cache size	: 512 KB
physical id	: 0
siblings	: 2
core id		: 0
cpu cores	: 2
apicid		: 0
initial apicid	: 0
fdiv_bug	: no
hlt_bug		: no
f00f_bug	: no
coma_bug	: no
fpu		: yes
fpu_exception	: yes
cpuid level	: 1
wp		: yes
flags		: fpu vme de pse msr pae mce cx8 apic mtrr pge mca cmov pat pse36 clflush mmx fxsr sse sse2 ht syscall nx mmxext fxsr_opt rdtscp lm 3dnowext 3dnow extd_apicid pni cx16 lahf_lm cmp_legacy svm extapic cr8_legacy 3dnowprefetch
bogomips	: 1892.35
clflush size	: 64
cache_alignment	: 64
address sizes	: 40 bits physical, 48 bits virtual
power management: ts fid vid ttp tm stc 100mhzsteps

processor	: 1
vendor_id	: AuthenticAMD
cpu family	: 15
model		: 104
model name	: AMD Turion(tm) 64 X2 Mobile Technology TL-58
stepping	: 1
cache size	: 512 KB
physical id	: 0
siblings	: 2
core id		: 1
cpu cores	: 2
apicid		: 1
initial apicid	: 1
fdiv_bug	: no
hlt_bug		: no
f00f_bug	: no
coma_bug	: no
fpu		: yes
fpu_exception	: yes
cpuid level	: 1
wp		: yes
flags		: fpu vme de pse msr pae mce cx8 apic mtrr pge mca cmov pat pse36 clflush mmx fxsr sse sse2 ht syscall nx mmxext fxsr_opt rdtscp lm 3dnowext 3dnow extd_apicid pni cx16 lahf_lm cmp_legacy svm extapic cr8_legacy 3dnowprefetch
bogomips	: 1896.44
clflush size	: 64
cache_alignment	: 64
address sizes	: 40 bits physical, 48 bits virtual
power management: ts fid vid ttp tm stc 100mhzsteps

---

### Post by Frogs Hair on 2011-01-02
On my AMD x II the total mhz for each core appears under stepping.

---

### Post by wojox on 2011-01-02
Have you added anything extra to the boot line?

---

### Post by cascade9 on 2011-01-02
I wonder if the CPU Mhz wil appear in lshw? (I doubt it, but worth a shot)

---

### Post by buntuyu on 2011-01-02
(To cascade9)
 	
> 
I wonder if the CPU Mhz wil appear in lshw? (I doubt it, but worth a shot)


Yes, it does.  Relevant snippet included below.

------------------------

(To wojox)

> 
Have you added anything extra to the boot line? 


Yes: I modified my kernel options in order to stop the gray-display system freezes. These are the options that worked for that; I restore them every time the kernel gets upgraded (and my grub.cfg gets wiped out):

linux   /vmlinuz-2.6.32-27-generic root=UUID=<blah blah> ro nomodeset notsc clocksource=hpet

------------------------

(To Frogs Hair)
 	
> 
On my AMD x II the total mhz for each core appears under stepping. 


1) Are you missing the "CPU MHz" line, too?
2) Do you have 32-bit Ubuntu installed on your AMD?


===============
snippet from lshw:

     *-cpu:0
          description: CPU
          product: AMD Turion(tm) 64 X2 Mobile Technology TL-58
          vendor: Advanced Micro Devices [AMD]
          physical id: 5
          bus info: cpu@0
          version: 15.8.1
          slot: Socket M2/S1G1
          size: 1900MHz
          capacity: 4GHz
          width: 64 bits
          clock: 200MHz
          capabilities: boot fpu fpu_exception wp vme de pse msr pae mce cx8 apic mtrr pge mca cmov pat pse36 clflush mmx fxsr sse sse2 ht syscall nx mmxext fxsr_opt rdtscp x86-64 3dnowext 3dnow extd_apicid pni cx16 lahf_lm cmp_legacy svm extapic cr8_legacy 3dnowprefetch cpufreq

---

### Post by wojox on 2011-01-02
To keep those options in a file, run

```
gksudo gedit /etc/default/grub
```

And add them to

```
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
```

And

```
sudo update-grub
```

This will keep you from having to manually add them when you get a new kernel. 

If your running nvidia and have the driver installed, you shouldn't need "nomodeset" anymore.

Maybe try disabling the Time Stamp Counter and see if it shows up then.

---

### Post by buntuyu on 2011-01-02
> **wojox said:**
> To keep those options in a file, run

If your running nvidia and have the driver installed, you shouldn't need "nomodeset" anymore.

Maybe try disabling the Time Stamp Counter and see if it shows up then.

Thanks for the tip on grub default. Do you mean try re-enabling TSC ?

I already have the "notsc" kernel option.  Are you suggesting I remove it and see what happens?

regarding NVidia -- I wish I did have NVidia; instead, I have:

   ATI Radeon Xpress 200M

(so, I'd still need "nomodeset", correct?)

thanks

---

### Post by wojox on 2011-01-02
> **buntuyu said:**
> Thanks for the tip on grub default. Do you mean try re-enabling TSC ?

I already have the "notsc" kernel option.  Are you suggesting I remove it and see what happens?

Yes try removing it and updating grub and reboot. Then run cpuinfo.

> **buntuyu said:**
> 
regarding NVidia -- I wish I did have NVidia; instead, I have:

   ATI Radeon Xpress 200M

(so, I'd still need "nomodeset", correct?)

You shouldn't once you driver is downloaded and activated. At least with nvidia that how it worked for me.

I've run the 32 bit kernel under my AMD 64 and never had that problem.

---

### Post by buntuyu on 2011-01-02
> **wojox said:**
> Yes try removing it and updating grub and reboot. Then run cpuinfo.

You shouldn't once you driver is downloaded and activated. At least with nvidia that how it worked for me.

I've run the 32 bit kernel under my AMD 64 and never had that problem.

removing "notsc" did it! THANKS!

(if my system resumes its freezes, I guess I'll start a whole NEW thread, but this one is solved :-))

---

