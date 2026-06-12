---
title: "cpu has svm, but cannot install 64bit host in 64bit lucid guest"
date: 2011-12-31
forum: General Help
---

### Post by garby on 2011-12-31
I am getting problem with virtualbox to install 64bit os to 64bit ubuntu lucid guest. Running any 64bit iso freezes.   

```
$ egrep '(vmx|svm)' --color=always /proc/cpuinfo 
flags        : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush mmx fxsr sse sse2 ht syscall nx mmxext fxsr_opt rdtscp lm 3dnowext 3dnow rep_good extd_apicid pni cx16 lahf_lm cmp_legacy [COLOR=Red]svm[/COLOR] extapic cr8_legacy 3dnowprefetch 

flags        : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush mmx fxsr sse sse2 ht syscall nx mmxext fxsr_opt rdtscp lm 3dnowext 3dnow rep_good extd_apicid pni cx16 lahf_lm cmp_legacy [COLOR=Red]svm[/COLOR] extapic cr8_legacy 3dnowprefetch
```

Could not figure out the problem!!! 

Thanks and Happy new year 2012 to all ubuntu family (developers, users and supporters).

---

