---
title: "Unusually hot running temperatures 11.10 64bit"
date: 2012-03-13
forum: General Help
---

### Post by ToshibaLaptoplinux on 2012-03-13
Summary says it all. I have a clean install of Ubuntu 11.10 64bit on a Samsung laptop. It is a dual boot wityh Windows 7. I noticed immediately it runs VERY hot.

These are the temps when running under Ubuntu:

$ sensors
acpitz-virtual-0
Adapter: Virtual device
temp1:        +60.0°C  (crit = +99.0°C)
temp2:        +29.8°C  (crit = +99.0°C)

radeon-pci-0100
Adapter: PCI adapter
temp1:        +62.0°C  

coretemp-isa-0000
Adapter: ISA adapter
Physical id 0:  +60.0°C  (high = +86.0°C, crit = +100.0°C)
Core 0:         +58.0°C  (high = +86.0°C, crit = +100.0°C)
Core 1:         +58.0°C  (high = +86.0°C, crit = +100.0°C)
Core 2:         +59.0°C  (high = +86.0°C, crit = +100.0°C)
Core 3:         +56.0°C  (high = +86.0°C, crit = +100.0°C)

These are the temperatures under Win 7. Note the huge spike in Ubuntu. It is over 15 degrees in some cases!:

|  +- CPU Core #1    :       41       38       42 (/intelcpu/0/temperature/0)
|  +- CPU Core #2    :       41       39       42 (/intelcpu/0/temperature/1)
|  +- CPU Core #3    :       41       39       43 (/intelcpu/0/temperature/2)
|  +- CPU Core #4    :       41       36       42 (/intelcpu/0/temperature/3)
|  +- CPU Package    :       42       40       43 (/intelcpu/0/temperature/4)

---

### Post by Gremlinzzz on 2012-03-13
old news, it is a kernel problem with certain hardware cause excessive heat.
I heard that the newest kernel in 12.04 Ubuntu solved the problem:popcorn:

---

### Post by 2F4U on 2012-03-13
Seems to me as if the graphics card could be at least partly responsible for the high temperature. What graphics driver are you using. The open source graphics drivers don't have a good power management implemented.

---

### Post by Mark Phelps on 2012-03-13
> **Gremlinzzz said:**
> old news, it is a kernel problem with certain hardware cause excessive heat.
I heard that the newest kernel in 12.04 Ubuntu solved the problem:popcorn:

Truly wish that were the case ...

Apparently, there are TWO different overheating problems, both kernel-related, and only the ones with the Sandy Bridge processor are fixed in 12.04.  The other ones are not.

---

### Post by ToshibaLaptoplinux on 2012-03-16
Although I don't know if the root cause of the problem is the same, I remember having this same problem with previous releases of Ubuntu in the past.

No matter how one looks at it, excessive heat is hardware's worst nightmare. I love Ubuntu and have been a LONG time user but clearly, at least for laptops, it isn't ready for primetime.

Can anyone point me to a temporary workaround to bring my operating temps down until the problem is fixed? How does Dell deal with this issue given they now offer their laptops with Ubuntu pre-installed?

I am willing to jump through some hoops to keep using Ubuntyu on my laptop but if their isn't a wsorkaround or solution I may have to look at another distro at least for my laptop.

---

### Post by superbike on 2012-03-16
try installing lighter ui like e17
also stopping unused daemons and apps may help

---

### Post by ToshibaLaptoplinux on 2012-03-23
> **superbike said:**
> try installing lighter ui like e17
also stopping unused daemons and apps may help

Thanks. I'll give it a shot and report back.

Is anyone out there running a dell laptop that came pre-installed with Ubuntu willing to report some of their operating temps? I wonder if Dell solved this problem if it is indeed a kernel issue. Or do they just let their boxes run hot?

---

### Post by ToshibaLaptoplinux on 2012-04-30
I tried this...

[http://ubuntuforums.org/showthread.php?t=1859945](http://ubuntuforums.org/showthread.php?t=1859945)

It didn't help in my particular case butI am posting it because it does seem to help in some situations.

I really hope a fix comes down the pipe for this problem soon.

---

