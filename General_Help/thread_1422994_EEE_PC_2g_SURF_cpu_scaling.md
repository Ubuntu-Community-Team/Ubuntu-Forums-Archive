---
title: "EEE PC 2g SURF cpu scaling"
date: 2010-03-06
forum: General Help
---

### Post by agolasol on 2010-03-06
hi!

i have eee pc 2g surf it has celerom m 800mhz underclock to 571mhz. and it was said as of now it cannot be overclock or back to 800mhz because it has other type of clock generator compare to other eee pc models.

i add the line p4_clockmod in '/etc/modules'

then: 

jok@jok:~$ cat /proc/cpuinfo
processor    : 0
vendor_id    : GenuineIntel
cpu family    : 6
model        : 13
model name    : Intel(R) Celeron(R) M processor          800MHz
stepping    : 8
cpu MHz        : 800.000
cache size    : 64 KB
fdiv_bug    : no
hlt_bug        : no
f00f_bug    : no
coma_bug    : no
fpu        : yes
fpu_exception    : yes
cpuid level    : 2
wp        : yes
flags        : fpu vme de pse tsc msr pae mce cx8 apic mtrr pge mca cmov clflush dts acpi mmx fxsr sse sse2 ss tm pbe nx up bts
bogomips    : 1139.87
clflush size    : 64
power management:

IS IT A REAL PROCESSOR SPEED FOR THIS EEE PC 2G SURF? THE CPU SCALING MONITOR APPLET DISPLAY ALSO 800MHZ.
IM RUNNING UBUNTU 9.10 IN SDHC.

jok@jok:~$ x86info
x86info v1.24.  Dave Jones 2001-2009
Feedback to <davej@redhat.com>.

Found 1 CPU
--------------------------------------------------------------------------
EFamily: 0 EModel: 0 Family: 6 Model: 13 Stepping: 8
CPU Model: Pentium M (Dothan) [C-0]
Processor name string: Intel(R) Celeron(R) M processor          800MHz
Type: 0 (Original OEM)    Brand: 2 (Intel® Pentium® III processor)
Number of cores per physical package=1
Number of logical processors per socket=1
Number of logical processors per core=1
APIC ID: 0x0    Package: 0  Core: 0   SMT ID 0
jok@jok:~$ 


PLS NEED CONFIRMATION.
THANkS iN ADVANCE

---

### Post by Intrepid Ibex on 2010-03-06
Well it is 800MHz now :D.

---

### Post by agolasol on 2010-03-06
maybe it is 800mhz now. it has improvement when im watching youtube. hope this will not overheat this lowend pc. so far fan and heating is normal in 6hours running. :)

---

