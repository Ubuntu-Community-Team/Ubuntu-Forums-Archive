---
title: "speedstep does not work but CPU freq scaling monitor claims it works"
date: 2011-06-12
forum: General Help
---

### Post by froff on 2011-06-12
hello
I use ubuntu 10.10 64bit on core2 duo machine.
Speedstep is enabled in bios.
Cpu frequency scaling monitor enables to choose frequency or performance profile.
But there is no effect on performance and core temperatures so it does _not_ work.
I test it by measuring duration of video compression process.

From the other side:
As I read I should have acpi-cpufreq or speedstep-centrino module loaded, and probably
cpufreq_ondemand,cpufreq_userspace,cpufreq_conservative,cpufreq_powersave as well.
lsmod does not report any of them.
When I try to load one, for example: "sudo modprobe speedstep-centrino" there is no information if there were any errors (no output at all) but lsmod still does not report this module loaded. What is going on? How to interpret this behavior?

---

### Post by mc4man on 2011-06-12
Are you saying it doesn't scale up or down?
what does this show
```
cat /proc/cpuinfo |grep MHz
```
```
cat /proc/cpuinfo |grep flags

```
To switch mode on say cpu0
```
cpufreq-selector -c 0 -g performance
```
```
cpufreq-selector -c 0 -g ondemand
```

---

### Post by pqwoerituytrueiwoq on 2011-06-12
i think speedstep lets the bios control the cpu speed preventing the os from doing it

disabling speedstep lets the os control the speed

---

### Post by froff on 2011-06-12
> **mc4man said:**
> Are you saying it doesn't scale up or down?
what does this show
```
cat /proc/cpuinfo |grep MHz
``````
cat /proc/cpuinfo |grep flags

```To switch mode on say cpu0
```
cpufreq-selector -c 0 -g performance
``````
cpufreq-selector -c 0 -g ondemand
```

Thank You for Your answer.

when 1800MHz is forced with scaling monitor:
```

cat /proc/cpuinfo |grep MHz
cpu MHz        : 1800.000
cpu MHz        : 1800.000

```when 1200MHz is forced with scaling monitor:
```

cat /proc/cpuinfo |grep MHz
cpu MHz        : 1800.000
cpu MHz        : 1200.000

```I think I know the reason:
Scaling monitor sets improper mode when I choose to force 1200MHz - probably leaves "on demand" mode so one core (activated one) is reported with 1800MHz.
When I set 1200MHz for both with cpufreq-selector (-f 1200000) everyting is as I expected: Performance drops in test.

Do You think I am right?

_[COLOR=black]Supplement:[/COLOR]_
O Gosh! Now I see that scaling monitor handles only one core at a time and need to be switched - I is not very convinient behavior.
I think now I know the reason of my problem definitely.

---

### Post by mc4man on 2011-06-12
well you could add two applets, one set to 0, the other to 1

Myself prefer to leave on the default of ondemand but lower the default up_theshold so I get upscaling a bit easier when needed (the kernel up theshold is 95 which is quite high, I use 75 here
 
(allows some videos to be played better, slightly faster response overall - may have a very slight affect of battery life but I don't use battery that often anymore (it's in need of replacing

---

