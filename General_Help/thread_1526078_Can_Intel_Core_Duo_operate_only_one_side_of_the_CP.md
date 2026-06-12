---
title: "Can Intel Core Duo operate only one side of the CPU?"
date: 2010-07-07
forum: General Help
---

### Post by [A]madeus on 2010-07-07
Hi experts,

Would you please help me check couple screenshots?
Does it mean my laptop is operating only one side of dual CPUs?

If yes, what possible it could be? i checked BIOS setting and it is supposed to operate on both CPUs.

[IMG]http://img96.imageshack.us/img96/1250/onecore.png[/IMG]


[IMG]http://img96.imageshack.us/img96/8837/cpuusage.png[/IMG]

My laptop is IBM T60 with Intel Core Duo processor T2300 (1.66 GHz).
It seems to me that it is operating merely one CPU so i'd need your help to confirm.

And please advice should there is any way to recover another side of the CPU (- -").

---

### Post by upbeat.linux on 2010-07-07
As a correction of terminology your processor is dual core which means there is one physical processor but two cores.

What is the output of:

```
cat /proc/cpuinfo
```

Also:

```
uname -ar
```

---

### Post by [A]madeus on 2010-07-08
Thank you [B]upbeat.linux
[/B]This evening i'll let you know the result :)

---

### Post by Yarui on 2010-07-08
I suppose the System Monitor could be reporting wrong, but you are right that your system isn't showing both cores.  Your CPU History graph should have 2 lines on it, one for each core.

---

### Post by [A]madeus on 2010-07-08
> **upbeat.linux said:**
> As a correction of terminology your processor is dual core which means there is one physical processor but two cores.

What is the output of:

```
cat /proc/cpuinfo
```Also:

```
uname -ar
```

Here it is;
```
[FONT=Courier New]amadeus@amadeus-laptop:~$ sudo cat /proc/cpuinfo
Password or swipe finger: 
processor : 0
vendor_id : GenuineIntel
cpu family    : 6
model     : 14
model name    : Genuine Intel(R) CPU           T2300  @ 1.66GHz
stepping  : 8
cpu MHz       : 1667.000
cache size    : 2048 KB
physical id   : 0
siblings  : 1
core id   : 0
cpu cores : 1
apicid    : 0
initial apicid  : 0
fdiv_bug  : no
hlt_bug   : no
f00f_bug  : no
coma_bug  : no
fpu       : yes
fpu_exception  : yes
cpuid level    : 10
wp        : yes
flags     : fpu vme de pse tsc msr pae mce cx8 mtrr pge mca cmov clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe nx constant_tsc arch_perfmon bts aperfmperf pni monitor est tm2 xtpr pdcm
bogomips    : 3324.75
clflush size    : 64
cache_alignment : 64
address sizes   : 32 bits physical, 32 bits virtual
power management:

amadeus@amadeus-laptop:~$ [/FONT] [FONT=Courier New]
amadeus@amadeus-laptop:~$ 
amadeus@amadeus-laptop:~$ 
amadeus@amadeus-laptop:~$ uname -ar
Linux amadeus-laptop 2.6.32-23-generic #37-Ubuntu SMP Fri Jun 11 07:54:58 UTC 2010 i686 GNU/Linux
amadeus@amadeus-laptop:~$ [/FONT]

```

---

### Post by dabl on 2010-07-08
It is only running one core.

I would test it with a Live CD, if you can, perhaps from another Linux distribution (there are lots).  If it only ever runs one core, I would say you have a broken T60.

---

### Post by davidmohammed on 2010-07-08
have a look in your BIOS - normally issues like this is because the various ACPI options you have are not enabled.

---

### Post by [A]madeus on 2010-07-08
> **davidmohammed said:**
> have a look in your BIOS - normally issues like this is because the various ACPI options you have are not enabled.
i've tried changing seem-to-be-related parameters in BIOS setting but it didn't get it work.
To be honest, i'm not sure if i comprehend enough of what the ACPI is. 

Should i go and check in Grub setting also? If yes, please explain me how.

@**dabi**
My laptop used to run Lucid Lynx with 2 cores operational.
i had played the system monitoring before and found it show two CPUs correctly.
It could be one core is now dead (as your assumption).

But i want to make sure it is not hidden.

---

### Post by upbeat.linux on 2010-07-08
You can find ACPI debugging information here:

[https://wiki.ubuntu.com/DebuggingACPI](https://wiki.ubuntu.com/DebuggingACPI)

I'd have to agree with davidmohammed; is ACPI disabled in the BIOS? If its enabled in grub disabled in the BIOS this might cause an issue or vice versa.

Check if there's initialization errors in dmesg:

```
dmesg | grep -i cpu
```

Once you work through the ACPI debug information you could try disabling Message Signal Interrupts in grub:

```
pci=nomsi
```

---

### Post by [A]madeus on 2010-07-09
> **upbeat.linux said:**
> You can find ACPI debugging information here:

[https://wiki.ubuntu.com/DebuggingACPI](https://wiki.ubuntu.com/DebuggingACPI)

I'd have to agree with davidmohammed; is ACPI disabled in the BIOS? If its enabled in grub disabled in the BIOS this might cause an issue or vice versa.

Check if there's initialization errors in dmesg:

```
dmesg | grep -i cpu
```Once you work through the ACPI debug information you could try disabling Message Signal Interrupts in grub:

```
pci=nomsi
```


Here is initialized errors;
```
amadeus@amadeus-laptop:~$ dmesg | grep -i cpu
[    0.158665] cpufreq-nforce2: No nForce2 chipset.
[    0.200081] ACPI: SSDT bfef1d36 00240 (v01  PmRef  Cpu0Ist 00000100 INTL 20050513)
[    0.200950] ACPI: SSDT bfef1ffb 0065A (v01  PmRef  Cpu0Cst 00000100 INTL 20050513)
[    0.208510] processor LNXCPU:00: registered as cooling_device0
[    0.500120] cpuidle: using governor ladder
[    0.500199] cpuidle: using governor menu
[   20.796965] [drm] GART: num cpu pages 131072, num gpu pages 131072
[   22.451850] CPU0 attaching NULL sched-domain.
[   22.451905] CPU0 attaching NULL sched-domain.
[   25.545862] CPU0 attaching NULL sched-domain.
[   25.545916] CPU0 attaching NULL sched-domain.

```

---

### Post by upbeat.linux on 2010-07-09
Have you tried booting with a Live CD to see if you have the same issue?  Have you tried running through the ACPI troubleshooting documentation?  

You could also try "reinstalling" a new version of the kernel:

```
sudo apt-get install linux-image
```

---

