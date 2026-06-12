---
title: "CPU Confusion"
date: 2010-11-21
forum: General Help
---

### Post by conradin on 2010-11-21
Hi all, 
I have a 2.8 Ghz pentium 4 CPU in a dell optiplex gx280.
I cant for the life of me figure out why I cnat get the full clock speed out of the thing. Below, you can see that although it says it is indeed a 2.8GHz processor, its only running at 1.4 Ghz.
I  read the article 
[http://embraceubuntu.com/2005/11/04/enabling-cpu-frequency-scaling/](http://embraceubuntu.com/2005/11/04/enabling-cpu-frequency-scaling/)
which has worked for me in the past, but in this instance nothing seems to work.
Does anyone have any ideas? Please help, TIA.

```

~# cat /proc/cpuinfo 
processor	: 0
vendor_id	: GenuineIntel
cpu family	: 15
model		: 2
model name	: Intel(R) Pentium(R) 4 CPU 2.80GHz
stepping	: 9
cpu MHz		: 1400.021
cache size	: 512 KB
fdiv_bug	: no
hlt_bug		: no
f00f_bug	: no
coma_bug	: no
fpu		: yes
fpu_exception	: yes
cpuid level	: 2
wp		: yes
flags		: fpu vme de pse tsc msr pae mce cx8 apic mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe up pebs bts cid xtpr
bogomips	: 2800.04
clflush size	: 64
cache_alignment	: 128
address sizes	: 36 bits physical, 32 bits virtual
power management:


```

---

### Post by tad1073 on 2010-11-21
It will run at full speed when needed, the feature is called cpu scaling which reduces power consumption and cpu cycles to extend the lifetime of the processor.

---

### Post by carl4926 on 2010-11-21
It looks OK to me

Try running: glxgears at full screen for 5 mins and check again

bogomips quote is correct too

---

### Post by conradin on 2010-11-21
I'm finding a consistent lack of performance here. Is there some way to force it to run faster? 
I have been using cpufreq-selector -f , which typically works, but instead I keep getting the "no freq support." output. 
```
# cpufreq-selector -f [some speed]
No cpufreq support

```

---

### Post by amauk on 2010-11-22
You can install stress to test what happens when your systm is under heavy load```
sudo apt-get install stress
```

Open up 3 terminal windows,

In first, run```
top
```
In second, run```
watch -n 1 'cat /proc/cpuinfo'
```
and in third run the stress tool```
stress --cpu 10 --io 10 --vm 10 --vm-bytes 128M --timeout 60s
```

Then see if the CPU scales up to full speed

---

### Post by conradin on 2010-11-22
Ok, Glxgears running full screen, Firefox and a few terminals this thing is lagging a bit, here is the cpuinfo:
```
cat /proc/cpuinfo 
processor	: 0
vendor_id	: GenuineIntel
cpu family	: 15
model		: 2
model name	: Intel(R) Pentium(R) 4 CPU 2.80GHz
stepping	: 9
cpu MHz		: 1400.021
cache size	: 512 KB
fdiv_bug	: no
hlt_bug		: no
f00f_bug	: no
coma_bug	: no
fpu		: yes
fpu_exception	: yes
cpuid level	: 2
wp		: yes
flags		: fpu vme de pse tsc msr pae mce cx8 apic mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe up pebs bts cid xtpr
bogomips	: 2800.04
clflush size	: 64
cache_alignment	: 128
address sizes	: 36 bits physical, 32 bits virtual
power management:
 
```

---

### Post by amauk on 2010-11-22
glxgears will only stress the GPU, not the CPU

---

### Post by carl4926 on 2010-11-22
> **amauk said:**
> glxgears will only stress the GPU, not the CPU

You might be right. But usually with my 2x core the second kicks in with rendering work.

OP
I defer to @amauk and suggest you try his suggestion:)

---

### Post by conradin on 2010-11-22
nope, its still running 1.4GHz.

> **amauk said:**
> You can install stress to test what happens when your systm is under heavy load```
sudo apt-get install stress
```

Open up 3 terminal windows,

In first, run```
top
```
In second, run```
watch -n 1 'cat /proc/cpuinfo'
```
and in third run the stress tool```
stress --cpu 10 --io 10 --vm 10 --vm-bytes 128M --timeout 60s
```

Then see if the CPU scales up to full speed

---

### Post by mc4man on 2010-11-22
Sorry is this begging the obvious - is this a desktop? 
I don't know what the speedstep flag is pre- 'enhanced SpeedsTep' - ('est'), but don't see that or any likely one for speedstep

---

### Post by amauk on 2010-11-22
Well,
Just browsing through the link in your 1st post
it's possible that you've manually set the CPU to 1.4GHz

Try rebooting and re-running stress

Also,
that article is 5 years old (Ie. 10 Ubuntu releases ago)
stuff that out of date usually does more harm than good

---

### Post by Decatf on 2010-11-22
> **mc4man said:**
> Sorry is this begging the obvious - is this a desktop? 
I don't know what the speedstep flag is pre- 'enhanced SpeedsTep' - ('est'), but don't see that or any likely one for speedstep

I don't think any Pentium 4 desktop chips had speedstep. Unless the op has a Pentium 4M.

---

### Post by mc4man on 2010-11-22
> I don't think any Pentium 4 desktop chips had speedstep. Unless the op has a Pentium 4M. 
That's why I asked - the Op should clear that up...
On my p4 - desktop, (on it right now), the only time it's ever run at less than full was when I'd forgotten to clean lint off of the top of the cpu heatsink for some time. In that case the cpu was scaling back to arrest the heat rise. 
(and in that particular case it was successful, but stayed at the reduced speed

---

### Post by conradin on 2010-11-22
I have some Pentium 4s which seem to support cpu-frequency selection, is this what the reference to speed step is? Granted 1 is a Pentium D and the others I'm not sure what they are. This is a Desktop I received from a friend, I checked the hardware it is indeed a 2.8GHz @ 800MHz FSB Pentium 4 CPU. Then I went into the BIOS, and its listed as a 1.4GHz CPU 400MHz FSB. I'm thinking this might be a limit on the motherboard. Theres prolly not much i can do about it though now is there?

---

### Post by conradin on 2010-11-22
OMFG, 
I Just installed a 1.4GHz 400MHz FSB, 256 cache  -- says it right on the chip. Checked in the Bios, yep, thats what it is. For Giggles, ran the code 
cat /proc/cpuinfo, and got: 1.6GHz
What eva, I think we are done here...
```

~$ cat /proc/cpuinfo 
processor	: 0
vendor_id	: GenuineIntel
cpu family	: 15
model		: 1
model name	: Intel(R) Pentium(R) 4 CPU 1.60GHz
stepping	: 2
cpu MHz		: 1600.075
cache size	: 256 KB
fdiv_bug	: no
hlt_bug		: no
f00f_bug	: no
coma_bug	: no
fpu		: yes
fpu_exception	: yes
cpuid level	: 2
wp		: yes
flags		: fpu vme de pse tsc msr pae mce cx8 apic mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm up pebs bts
bogomips	: 3200.15
clflush size	: 64
cache_alignment	: 128
address sizes	: 36 bits physical, 32 bits virtual
power management:


```

---

