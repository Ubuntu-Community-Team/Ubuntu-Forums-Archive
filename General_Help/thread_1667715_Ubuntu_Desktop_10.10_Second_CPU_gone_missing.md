---
title: "Ubuntu Desktop 10.10 Second CPU gone missing"
date: 2011-01-15
forum: General Help
---

### Post by syednaim on 2011-01-15
Hi,
I installed Ubuntu Desktop 10.10 AMD64 on MSI-9130 K8T Master with 2 Opteron 246 CPU's. But System monitor shows only one CPU and out put of cat /proc/cpuinfo is as folows

syed@syed-desktop:~$ cat /proc/cpuinfo
processor    : 0
vendor_id    : AuthenticAMD
cpu family    : 15
model        : 5
model name    : AMD Opteron(tm) Processor 246   
stepping    : 10
cpu MHz        : 1992.871
cache size    : 1024 KB
fpu        : yes
fpu_exception    : yes
cpuid level    : 1
wp        : yes
flags        : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush mmx fxsr sse sse2 syscall nx mmxext lm 3dnowext 3dnow rep_good
bogomips    : 3985.74
TLB size    : 1024 4K pages
clflush size    : 64
cache_alignment    : 64
address sizes    : 40 bits physical, 48 bits virtual
power management: ts fid vid ttp

Please help me to solve this issue.

Regards
Syed

---

### Post by davidmohammed on 2011-01-15
sometimes you have to boot with one of the following boot options


acpi=ht
acpi=off

to try - press shift on booting.  Press e to edit.  Add one of the above immediately before the text "quiet splash"

then

CTRL+X to boot.

---

### Post by tosk on 2011-01-15
Is your BIOS set to expose both CPUs?

Also, do you have a recent stable version of the kernel installed? If you've done a recent update, then 'yes.'

---

### Post by syednaim on 2011-01-15
Thanks for the reply.. 
Yes my BIOS is set to expose both CPU's.
I had this problem when I installed this OS, later I upgraded kernel thinking that it will resolve the problem.

---

### Post by syednaim on 2011-01-15
Thanks for the reply davidmohammed. Do I have to add those lines somewhere?

---

### Post by syednaim on 2011-01-15
> **davidmohammed said:**
> sometimes you have to boot with one of the following boot options


acpi=ht
acpi=off

to try - press shift on booting.  Press e to edit.  Add one of the above immediately before the text "quiet splash"

then

CTRL+X to boot.

Tried both options no effect. Kernel version I am using is
Linux syed-desktop 2.6.35-24-generic #42-Ubuntu SMP Thu Dec 2 02:41:37 UTC 2010 x86_64 GNU/Linux

---

### Post by davidmohammed on 2011-01-15
> **syednaim said:**
> Tried both options no effect. Kernel version I am using is
Linux syed-desktop 2.6.35-24-generic #42-Ubuntu SMP Thu Dec 2 02:41:37 UTC 2010 x86_64 GNU/Linux

type 
uname -r


have you compiled this kernel yourself?

What instructions did you use to compile?

---

### Post by syednaim on 2011-01-15
> **davidmohammed said:**
> type 
uname -r


have you compiled this kernel yourself?

What instructions did you use to compile?

2.6.35-24-generic
No I installed using "sudo apt-get install  kernel-generic"

---

### Post by syednaim on 2011-01-15
> **davidmohammed said:**
> type 
uname -r


have you compiled this kernel yourself?

What instructions did you use to compile?

2.6.35-24-generic
No I did not compile. I installed using "sudo apt-get install  kernel-generic"

---

### Post by syednaim on 2011-01-15
> **davidmohammed said:**
> type 
uname -r


have you compiled this kernel yourself?

What instructions did you use to compile?

2.6.35-24-generic
No I did not compile. I installed using "sudo apt-get install  kernel-generic"

---

### Post by davidmohammed on 2011-01-15
you mentioned you tried another kernel

what was this?

Can I suggest you try the 2.6.37rc2-maverick kernel from [here]("https://wiki.ubuntu.com/KernelTeam/MainlineBuilds?action=show&redirect=KernelMainlineBuilds")

You mentioned you are running 64bit - therefore follow the installation instructions and download the amd64 deb files not the i386 deb files.

---

