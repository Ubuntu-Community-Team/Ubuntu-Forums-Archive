---
title: "Intel CPU Virtualization Freezes System"
date: 2009-10-28
forum: General Help
---

### Post by nmueller on 2009-10-28
Hi there,

I use a Shuttle Barebone and have some problems with virtualization and vmware. Basically everything works fine, but as soon as I turn of Hardware Virtualization in the BIOS my system (vmware and ubuntu) freezes, when I start a vm. Do you have any ideas why this could be a problem?

lshw gave me this output:
```

  *-core
       description: Motherboard
       product: FX38
       vendor: Shuttle
       physical id: 0
       version: V10
       serial: 0
       slot: &#65533;PRIMARY IDE
     *-firmware
          description: BIOS
          vendor: Phoenix Technologies, LTD
          physical id: 0
          version: 6.00 PG (03/10/2008)
          size: 128KiB
          capacity: 960KiB
          capabilities: isa pci pnp apm upgrade shadowing cdboot bootselect socketedrom edd int13floppy360 int13floppy1200 int13floppy720 int13floppy2880 int5printscreen int9keyboard int14serial int17printer int10video acpi usb ls120boot zipboot biosbootspecification
     *-cpu
          description: CPU
          product: 06/17
          vendor: Intel Corp.
          physical id: 5
          bus info: cpu@0
          slot: Socket 775
          size: 2831MHz
          capacity: 4GHz
          width: 64 bits
          clock: 333MHz
          capabilities: fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe syscall nx x86-64 constant_tsc arch_perfmon pebs bts rep_good pni dtes64 monitor ds_cpl vmx smx est tm2 ssse3 cx16 xtpr pdcm sse4_1 xsave lahf_lm tpr_shadow vnmi flexpriority
        *-cache:0
             description: L1 cache
             physical id: b
             slot: Internal Cache
             size: 32KiB
             capacity: 32KiB
             capabilities: synchronous internal write-back
        *-cache:1 DISABLED
             description: L2 cache
             physical id: c
             slot: External Cache
             capabilities: synchronous external write-back

```

I'm running Ubuntu 9.04 with Kernel 2.6.28-16-generic.

Any ideas?

---

### Post by P4man on 2009-10-28
What cpu is that? It may not have hardware virtualization extensions.
Another thought would be upgrading your bios, as its weird  it detects your cpu type as "product: 06/17" rather than something like "Intel(R) Core(TM)2 CPU"  so Im wondering if it has proper support for your cpu.

---

### Post by nmueller on 2009-10-28
Didn't notice that thanks. The CPU is a Intel Core 2 Quad Q9550 (2833) Quad Core.

Well I'm trying to update the BIOS even tough there is nothing about virtualization in the changelog.

---

### Post by albandy on 2009-10-28
Maybe becasue vmware is using the vmx extension of your cpu, if you disable the vmx extension (hw virtualization) and you have configured (or autoconfigured) the virtual machine to use vmx it's normal that the machine gets freezed.

---

### Post by nmueller on 2009-10-28
well it freezes, if i enable hardware virtualization in the BIOS not the other way.

---

### Post by P4man on 2009-10-28
It wouldnt have to mention that explicitly but I would expect it to include support for newer cpu's and it looks like your bios predates the q9550 (not sure if that bios date is US or EU formatted date). Such a bios may work well enough for most things, but perhaps not for this.

---

### Post by albandy on 2009-10-28
in the main system type cat /proc/cpuinfo
and paste it here.

---

### Post by revanb on 2009-10-28
I also have the Q9550 and it does support virtualization extensions. I use it with Virtualbox. I have not had problems, but I did upgrade my BIOS immediately before doing anything else really.

---

### Post by nmueller on 2009-10-28
@P4man Ok, Hope the BIOS update will help.

@albandy
Here is the output of cat /proc/cpuinfo
```

processor    : 0
vendor_id    : GenuineIntel
cpu family    : 6
model        : 23
model name    : 06/17
stepping    : 10
cpu MHz        : 2829.608
cache size    : 6144 KB
physical id    : 0
siblings    : 4
core id        : 0
cpu cores    : 4
apicid        : 0
initial apicid    : 0
fpu        : yes
fpu_exception    : yes
cpuid level    : 13
wp        : yes
flags        : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe syscall nx lm constant_tsc arch_perfmon pebs bts rep_good pni dtes64 monitor ds_cpl vmx smx est tm2 ssse3 cx16 xtpr pdcm sse4_1 xsave lahf_lm tpr_shadow vnmi flexpriority
bogomips    : 5659.21
clflush size    : 64
cache_alignment    : 64
address sizes    : 36 bits physical, 48 bits virtual
power management:

processor    : 1
vendor_id    : GenuineIntel
cpu family    : 6
model        : 23
model name    : 06/17
stepping    : 10
cpu MHz        : 2829.608
cache size    : 6144 KB
physical id    : 0
siblings    : 4
core id        : 3
cpu cores    : 4
apicid        : 3
initial apicid    : 3
fpu        : yes
fpu_exception    : yes
cpuid level    : 13
wp        : yes
flags        : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe syscall nx lm constant_tsc arch_perfmon pebs bts rep_good pni dtes64 monitor ds_cpl vmx smx est tm2 ssse3 cx16 xtpr pdcm sse4_1 xsave lahf_lm tpr_shadow vnmi flexpriority
bogomips    : 5659.25
clflush size    : 64
cache_alignment    : 64
address sizes    : 36 bits physical, 48 bits virtual
power management:

processor    : 2
vendor_id    : GenuineIntel
cpu family    : 6
model        : 23
model name    : 06/17
stepping    : 10
cpu MHz        : 2829.608
cache size    : 6144 KB
physical id    : 0
siblings    : 4
core id        : 1
cpu cores    : 4
apicid        : 1
initial apicid    : 1
fpu        : yes
fpu_exception    : yes
cpuid level    : 13
wp        : yes
flags        : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe syscall nx lm constant_tsc arch_perfmon pebs bts rep_good pni dtes64 monitor ds_cpl vmx smx est tm2 ssse3 cx16 xtpr pdcm sse4_1 xsave lahf_lm tpr_shadow vnmi flexpriority
bogomips    : 5659.24
clflush size    : 64
cache_alignment    : 64
address sizes    : 36 bits physical, 48 bits virtual
power management:

processor    : 3
vendor_id    : GenuineIntel
cpu family    : 6
model        : 23
model name    : 06/17
stepping    : 10
cpu MHz        : 2829.608
cache size    : 6144 KB
physical id    : 0
siblings    : 4
core id        : 2
cpu cores    : 4
apicid        : 2
initial apicid    : 2
fpu        : yes
fpu_exception    : yes
cpuid level    : 13
wp        : yes
flags        : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe syscall nx lm constant_tsc arch_perfmon pebs bts rep_good pni dtes64 monitor ds_cpl vmx smx est tm2 ssse3 cx16 xtpr pdcm sse4_1 xsave lahf_lm tpr_shadow vnmi flexpriority
bogomips    : 5659.23
clflush size    : 64
cache_alignment    : 64
address sizes    : 36 bits physical, 48 bits virtual
power management:

```

@revanb Great to hear! I hope everything will be fixed after the BIOS update!

---

### Post by albandy on 2009-10-28
Your processor have the vmx fag, this  means that you processor have virtualization extensions. Is enabled the BIOS virtualization option?

---

### Post by nmueller on 2009-10-28
@all
Ok the BIOS Update did the trick. Everything works now! Thanks for the help

---

### Post by P4man on 2009-10-28
Great. Out of curiosity and to learn from this, does lshw now give a proper description of your C2Q ?

---

### Post by nmueller on 2009-10-28
Yes. Now it displays the correct CPU description.

---

