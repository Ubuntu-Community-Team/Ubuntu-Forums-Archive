---
title: "2MB RAM and still slow!"
date: 2009-09-27
forum: General Help
---

### Post by t0p on 2009-09-27
I recently upgraded RAM on my computers - so my desktop machine has 624MB RAM, and my EeePC 701 has 2GB.

The desktop computer (Pentium 4 1.7GHz) is now pretty quick.  The EeePC has also sped up loads for some tasks.  But it's still slow on others.  A big example is when I run a command with sudo there's a very long pause before the command runs.

What can I do to fix this?  Or is this just to be expected with the Celeron M?

Note: desktop with Pentium 4 1.7GHz + 640MB RAM, EeePC with Celeron M 900MHz + 2GB RAM

---

### Post by kerry_s on 2009-09-27
i thought the 701 was clocked at 600mhz?

do a "cat /proc/cpuinfo" & post the output.

---

### Post by t0p on 2009-09-27
> **kerry_s said:**
> i thought the 701 was clocked at 600mhz?

do a "cat /proc/cpuinfo" & post the output.

It's *under*clocked to 600MHz, but you can crank it back up to 900MHz when your using Eeebuntu - maybe if you just use the array kernel in otherwise vanilla ubuntu.  Maybe even higher: I don't know if "Super High Performance" in acpi tools means 900 or something even higher... but it's higher than 600 anyway.

EDIT:

```
t0p@machine:~$ cat /proc/cpuinfo
processor    : 0
vendor_id    : GenuineIntel
cpu family    : 6
model        : 13
model name    : Intel(R) Celeron(R) M processor          900MHz
stepping    : 8
cpu MHz        : 900.000
cache size    : 512 KB
fdiv_bug    : no
hlt_bug        : no
f00f_bug    : no
coma_bug    : no
fpu        : yes
fpu_exception    : yes
cpuid level    : 2
wp        : yes
flags        : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat clflush dts acpi mmx fxsr sse sse2 ss tm pbe nx up bts
bogomips    : 1260.20
clflush size    : 64
```

---

### Post by simartem on 2009-09-27
The title says "2 MB Ram and still slow" :)
I thought "what would be more with only 2 megabytes ?" but i see that the RAM is 2 Gigs.
I believe there must have been a configuration problem to have the os running so slow.. I wish you cope with it soon.

---

### Post by t0p on 2009-09-27
> **simartem said:**
> The title says "2 MB Ram and still slow" :)
I thought "what would be more with only 2 megabytes ?" but i see that the RAM is 2 Gigs.

Duh!  How silly I am.  No option to edit thread title eh?

> **simartem said:**
> 
I believe there must have been a configuration problem or something because my ubuntu is working like hell in my pentium 4 @ 2.4 Ghz with 1,5 GB RAM with onboard ATI Radeon 128 Mb display. So quick really.

Yeah, that's why I posted this.  Not sure if it's the netbook's baby processor that's the problem or what.  Like I already said, my P4 1.7GHz with 624MB is quick - quicker than the netbook at some things.

The pause after a sudo command might indicate something: but I don't know what.  Surely someone here knows.

---

### Post by akakingess on 2009-09-27
Last time I tried, I was able to edit the thread title if you want to. Sorry I don't have anything constructive to help you with, but you maybe can edit the thread title:)

---

### Post by simartem on 2009-09-27
which version of ubuntu is the one you are running on the slow pc ? Did you try newest onez like 9.0.4 and Karmic Koala ?

---

### Post by t0p on 2009-09-27
> **simartem said:**
> which version of ubuntu is the one you are running on the slow pc ? Did you try newest onez like 9.0.4 and Karmic Koala ?

It's 9.04.  I'm not going to try Karmic yet.  Though I may when the final comes out, if this slowness doesn't go.

---

