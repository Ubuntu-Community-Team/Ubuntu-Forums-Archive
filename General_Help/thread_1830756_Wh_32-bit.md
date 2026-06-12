---
title: "Wh 32-bit?"
date: 2011-08-22
forum: General Help
---

### Post by Gwaro on 2011-08-22
Why does Ubuntu recommend a 32-bit version for download?

---

### Post by TBABill on 2011-08-22
Because it is a single solution that serves the widest range of computers, whereas 64 bit requires system compatibility checks to verify equipment is 64 bit capable. I would guess it is to help minimize problems or complaints for those users whose equipment can only handle a 32 bit OS.
 
Most modern hardware is capable of handling 64 bit, but it's a personal choice whether to run 32 or 64 bit. I have found no compatibility or hardware issues with 64 bit and I run it exclusively on my various machines, but others prefer 32 bit and in general application the difference is invisible. Heavier number crunching is where you may see the performance gain in 64 bit over 32 bit, particularly in graphical applications, both image and video editing. 
 
You can't go wrong either way. For high RAM amounts over 4GB I would recommend 64 bit instead of using a PAE kernel, but only because Phoronix tests concluded the 64 bit kernel was faster than the PAE 32 bit kernel. Best would be to try both and see what works best on your equipment.

---

### Post by Gwaro on 2011-08-22
> **TBABill said:**
> Because it is a single solution that serves the widest range of computers, whereas 64 bit requires system compatibility checks to verify equipment is 64 bit capable. I would guess it is to help minimize problems or complaints for those users whose equipment can only handle a 32 bit OS.
 
Most modern hardware is capable of handling 64 bit, but it's a personal choice whether to run 32 or 64 bit. I have found no compatibility or hardware issues with 64 bit and I run it exclusively on my various machines, but others prefer 32 bit and in general application the difference is invisible. Heavier number crunching is where you may see the performance gain in 64 bit over 32 bit, particularly in graphical applications, both image and video editing. 
 
You can't go wrong either way. For high RAM amounts over 4GB I would recommend 64 bit instead of using a PAE kernel, but only because Phoronix tests concluded the 64 bit kernel was faster than the PAE 32 bit kernel. Best would be to try both and see what works best on your equipment.

Thank you for  your reply.I would like to know my  kernel type;whether my machine can support 64-bit(am using 32-bit currently).How do i do it?

---

### Post by Script Warlock on 2011-08-22
grep --color=always -iw lm /proc/cpuinfo

a good [documentation]("https://help.ubuntu.com/community/32bit_and_64bit") regarding 32 and 64bit ubuntu

---

### Post by Gwaro on 2011-08-22
> **Script Warlock said:**
> grep --color=always -iw lm /proc/cpuinfo

could you translate this output for me:

mr@RIsk:~$ grep --color=always -iw lm /proc/cpuinfo
flags        : fpu vme de pse tsc msr pae mce cx8 apic mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe nx lm constant_tsc arch_perfmon pebs bts aperfmperf pni dtes64 monitor ds_cpl vmx est tm2 ssse3 cx16 xtpr pdcm sse4_1 xsave lahf_lm ida dts tpr_shadow vnmi flexpriority
flags        : fpu vme de pse tsc msr pae mce cx8 apic mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe nx lm constant_tsc arch_perfmon pebs bts aperfmperf pni dtes64 monitor ds_cpl vmx est tm2 ssse3 cx16 xtpr pdcm sse4_1 xsave lahf_lm ida dts tpr_shadow vnmi flexpriority

---

### Post by oldos2er on 2011-08-22
The 'lm' flag means your CPU is capable of running 64-bit.

---

