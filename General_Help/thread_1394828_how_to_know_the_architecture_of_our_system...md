---
title: "how to know the architecture of our system.."
date: 2010-01-31
forum: General Help
---

### Post by ershibbu on 2010-01-31
guys i have problem ..
whenever i go for download any offline packages 
than available in three architure
1.[U]i386
2.amd64
3.lpia

i had tried 1386 , lpia for wine both r not supported give error..
[/U]

---

### Post by claracc on 2010-01-31
In a xterm you type the command uname -a, it gives kernel version and system architecture.

---

### Post by SemiBuz on 2010-01-31
```
uname -m

```

---

### Post by ershibbu on 2010-01-31
> **SemiBuz said:**
> ```
uname -m

```

where in terminal or else???

---

### Post by SemiBuz on 2010-01-31
> **ershibbu said:**
> where in terminal or else???

Yes.

---

### Post by ershibbu on 2010-01-31
It's too strange it's i686..
N when i search for app. These r available only in three formets
1.i386
2.amd64
3.lpia

which architecture suite my system???????

---

### Post by SemiBuz on 2010-01-31
32bit ( i386 ) - if it doesn't work, try amd64 .. Personally, x86_64 confuses me - I can run both, 32bit and 64bit applications.

---

### Post by howefield on 2010-01-31
> **ershibbu said:**
> which architecture suite my system???????

You want the i386 version.

---

### Post by ershibbu on 2010-01-31
can any give the direct downloding link (offline) vlc media player for my system(i686)..

---

### Post by SemiBuz on 2010-01-31
[http://packages.ubuntu.com/karmic/i386/vlc/download](http://packages.ubuntu.com/karmic/i386/vlc/download)

---

### Post by oldos2er on 2010-01-31
ershibbu, can you run **cat /proc/cpuinfo** in a terminal, and post the output here?

---

### Post by ershibbu on 2010-01-31
HERE IS THE RESULT OF THE RESPECTED COMMAND: cat /proc/cpuinfo

er@er-desktop:~$ cat /proc/cpuinfo
processor    : 0
vendor_id    : GenuineIntel
cpu family    : 15
model        : 4
model name    : Intel(R) Pentium(R) D CPU 2.80GHz
stepping    : 7
cpu MHz        : 2800.276
cache size    : 1024 KB
physical id    : 0
siblings    : 2
core id        : 0
cpu cores    : 2
apicid        : 0
initial apicid    : 0
fdiv_bug    : no
hlt_bug        : no
f00f_bug    : no
coma_bug    : no
fpu        : yes
fpu_exception    : yes
cpuid level    : 5
wp        : yes
flags        : fpu vme de pse tsc msr pae mce cx8 apic mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe nx lm constant_tsc pebs bts pni dtes64 monitor ds_cpl cid cx16 xtpr lahf_lm
bogomips    : 5600.55
clflush size    : 64
power management:

processor    : 1
vendor_id    : GenuineIntel
cpu family    : 15
model        : 4
model name    : Intel(R) Pentium(R) D CPU 2.80GHz
stepping    : 7
cpu MHz        : 2800.276
cache size    : 1024 KB
physical id    : 0
siblings    : 2
core id        : 1
cpu cores    : 2
apicid        : 1
initial apicid    : 1
fdiv_bug    : no
hlt_bug        : no
f00f_bug    : no
coma_bug    : no
fpu        : yes
fpu_exception    : yes
cpuid level    : 5
wp        : yes
flags        : fpu vme de pse tsc msr pae mce cx8 apic mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe nx lm constant_tsc pebs bts pni dtes64 monitor ds_cpl cid cx16 xtpr lahf_lm
bogomips    : 5600.62
clflush size    : 64
power management:

---

### Post by oldos2er on 2010-01-31
Your processor is capable of running 64-bit Ubuntu, should you want to install it.

---

### Post by ershibbu on 2010-01-31
> **oldos2er said:**
> Your processor is capable of running 64-bit Ubuntu, should you want to install it.

brother can u tell me hpow u know my system is supports 64 bit...
i have cd ubuntu9.10..
and for 64 bit reinstall ubuntu or req. for 64 bit ubuntu..

---

### Post by SuperSonic4 on 2010-01-31
Be wary of uname -m. It will tell you the kernel of the OS installed rather than what the CPU can handle.

oldos2er's reply is a good one.

If you want VLC I would not bother with ubuntu's packaging as it'll be out of date (VLC 1.0.5 was released today)

Ubuntu instructions: [http://www.videolan.org/vlc/download-ubuntu.html](http://www.videolan.org/vlc/download-ubuntu.html)

Source Code: [http://www.videolan.org/vlc/download-sources.html](http://www.videolan.org/vlc/download-sources.html)

Git (bleeding edge/unstable): [http://wiki.videolan.org/Git#Basic_Git_usage](http://wiki.videolan.org/Git#Basic_Git_usage)

==========================================

edit: ```
model name : Intel(R) Pentium(R) D CPU 2.80GHz
``` and the fact it is showing two cores means 64 bit capable. Also you don't *have* to run 64 bit if you'd rather not but there isn't much reason not to

---

### Post by howefield on 2010-01-31
> **ershibbu said:**
> brother can u tell me hpow u know my system is supports 64 bit...

The "lm" flag indicates you have a 64 bit capable processor.

---

