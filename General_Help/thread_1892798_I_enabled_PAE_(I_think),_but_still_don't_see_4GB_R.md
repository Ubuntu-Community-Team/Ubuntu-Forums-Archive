---
title: "I enabled PAE (I think), but still don't see 4GB RAM. Why?"
date: 2011-12-08
forum: General Help
---

### Post by lethalfang on 2011-12-08
Any ideas why? It's pretty old computer: Dell PowerEdge SC420. 


```

uname -a; free -m

Linux HOME 2.6.32-36-generic-pae #79-Ubuntu SMP Tue Nov 8 23:25:26 UTC 2011 i686 GNU/Linux
             total       used       free     shared    buffers     cached
Mem:          3393       2450        942          0        424       1247
-/+ buffers/cache:        778       2614
Swap:         9985          0       9985

```


CPU Info:
```

processor	: 0
vendor_id	: GenuineIntel
cpu family	: 15
model		: 4
model name	: Intel(R) Pentium(R) 4 CPU 2.80GHz
stepping	: 1
cpu MHz		: 2792.975
cache size	: 1024 KB
physical id	: 0
siblings	: 2
core id		: 0
cpu cores	: 1
apicid		: 0
initial apicid	: 0
fdiv_bug	: no
hlt_bug		: no
f00f_bug	: no
coma_bug	: no
fpu		: yes
fpu_exception	: yes
cpuid level	: 5
wp		: yes
flags		: fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe nx constant_tsc pebs bts pni dtes64 monitor ds_cpl cid xtpr
bogomips	: 5585.95
clflush size	: 64
cache_alignment	: 128
address sizes	: 36 bits physical, 32 bits virtual
power management:

```

---

### Post by papibe on 2011-12-08
Could you post the result of these commands?
```
uname -a

apt-cache policy linux-generic-pae
```
Regards.

---

### Post by lethalfang on 2011-12-08
```

apt-cache policy linux-generic-pae

linux-generic-pae:
  Installed: 2.6.32.36.42
  Candidate: 2.6.32.36.42
  Version table:
 *** 2.6.32.36.42 0
        500 http://us.archive.ubuntu.com/ubuntu/ lucid-updates/main Packages
        500 http://us.archive.ubuntu.com/ubuntu/ lucid-security/main Packages
        100 /var/lib/dpkg/status
     2.6.32.21.22 0
        500 http://us.archive.ubuntu.com/ubuntu/ lucid/main Packages

```


```

Linux HOME 2.6.32-36-generic-pae #79-Ubuntu SMP Tue Nov 8 23:25:26 UTC 2011 i686 GNU/Linux

```

Thanks.

---

### Post by dcstar on 2011-12-09
> **lethalfang said:**
> Any ideas why? It's pretty old computer: Dell PowerEdge SC420. 
........

Probably for exactly the same reasons that already have been explained in the hundreds of threads already addressing this issue. Search them out.

---

### Post by lethalfang on 2011-12-09
> **dcstar said:**
> Probably for exactly the same reasons that already have been explained in the hundreds of threads already addressing this issue. Search them out.

Such as?
I did lots of searches and didn't find anything.

---

### Post by 73ckn797 on 2011-12-09
Here is a search link: [http://www.googlubuntu.com/](http://www.googlubuntu.com/) See what you get with this search entry: ```
pae kernal does not show all of the RAM
```

PAE is enabled on 1 of my computers that are 32 bit. It has 4Gb RAM but will only show as high as 3.9. When installing Ubuntu the PAE kernel was automatically installed. On my 32bit laptop with 2Gb RAM the kernel was not needed and was not installed. You will not see the full RAM capacity. I have had the system only show 3.6Gb of 4Gb.

PAE enabled kernels should be listed in Synaptic Package Manager.

---

### Post by lethalfang on 2011-12-10
> **73ckn797 said:**
> Here is a search link: [http://www.googlubuntu.com/](http://www.googlubuntu.com/) See what you get with this search entry: ```
pae kernal does not show all of the RAM
```

PAE is enabled on 1 of my computers that are 32 bit. It has 4Gb RAM but will only show as high as 3.9. When installing Ubuntu the PAE kernel was automatically installed. On my 32bit laptop with 2Gb RAM the kernel was not needed and was not installed. You will not see the full RAM capacity. I have had the system only show 3.6Gb of 4Gb.

PAE enabled kernels should be listed in Synaptic Package Manager.

Well, it seems like my BIOS isn't supporting PAE. 
My BIOS version is Feb. 2006..... and Dell doesn't seem to have a BIOS update anymore for that old box..... on well.

---

