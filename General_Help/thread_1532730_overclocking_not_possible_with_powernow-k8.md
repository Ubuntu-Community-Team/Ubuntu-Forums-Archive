---
title: "overclocking not possible with powernow-k8?"
date: 2010-07-16
forum: General Help
---

### Post by opt1k on 2010-07-16
Im trying to overclock my system and I cannot find a conclusive answer to this issue.

It appears that I need to compile a custom kernel, is there a way around this?

Heres my issue.

$ dmesg | grep MHz
[    0.000000] Detected 2024.936 MHz processor.
[    0.477840] powernow-k8:    0 : fid 0xa (1800 MHz), vid 0x6
[    0.477843] powernow-k8:    1 : fid 0x2 (1000 MHz), vid 0x12


As you can see the first line shows the overclock.  powernow-k8 is preventing this overclock.

$ cat /proc/cpuinfo | grep MHz
cpu MHz		: 1800.000


So where do I go from here without compiling a custom kernel and removing powernow-k8 from it?

Is there a workaround to this?  There is no setting in my bios either. ECS NFROCE3-A system board.

Ubuntu 10.04LTS

---

### Post by dcstar on 2010-07-17
> **opt1k said:**
> Im trying to overclock my system and I cannot find a conclusive answer to this issue.

It appears that I need to compile a custom kernel, is there a way around this?

Heres my issue.

$ dmesg | grep MHz
[    0.000000] Detected 2024.936 MHz processor.
[    0.477840] powernow-k8:    0 : fid 0xa (1800 MHz), vid 0x6
[    0.477843] powernow-k8:    1 : fid 0x2 (1000 MHz), vid 0x12


As you can see the first line shows the overclock.  powernow-k8 is preventing this overclock.

$ cat /proc/cpuinfo | grep MHz
cpu MHz		: 1800.000


So where do I go from here without compiling a custom kernel and removing powernow-k8 from it?

Is there a workaround to this?  There is no setting in my bios either. ECS NFROCE3-A system board.

Ubuntu 10.04LTS

Huh?, the clock speed is set as per the system requirements, if there is no demand on the CPU core then it is automatically throttled back.

If you want to waste power by having all your CPU cores running 100% all of the time then there are simple ways to achieve that.

---

### Post by opt1k on 2010-07-17
> **dcstar said:**
> Huh?, the clock speed is set as per the system requirements, if there is no demand on the CPU core then it is automatically throttled back.



If you want to waste power by having all your CPU cores running 100% all of the time then there are simple ways to achieve that.

???  I don't think you understood the issue.

This is a single core, Its overclocked from 1.8ghz to 2.0ghz.
  
[B][ 0.000000] Detected 2024.936 MHz processor.
[ 0.477840] powernow-k8: 0 : fid 0xa (1800 MHz), vid 0x6
[ 0.477843] powernow-k8: 1 : fid 0x2 (1000 MHz), vid 0x12[/B]

It will not run over 1.8ghz with "powernow-k8" yet the clock is 2024.936Mhz

I would be fine with it if powernow-k8 would allow running at 2ghz but it does not.

---

### Post by dino99 on 2010-07-17
who dont understood the issue ? :lolflag:

---

