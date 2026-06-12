---
title: "kvm fails to install on jaunty"
date: 2009-07-19
forum: General Help
---

### Post by hyperyoda on 2009-07-19
Setting up kvm (1:84+dfsg-0ubuntu12.3) ...
 * Loading kvm module kvm_amd                                                                                                                                                  FATAL: Error inserting kvm_amd (/lib/modules/2.6.28-13-generic/kernel/arch/x86/kvm/kvm-amd.ko): Operation not supported
                                                                                                                                                                        [fail]
invoke-rc.d: initscript kvm, action "start" failed.

My machine is AMD Athlon 64-bit but 32-bit kernel is installed.

root@hyperyoda:~# uname -a
Linux hyperyoda 2.6.28-13-generic #45-Ubuntu SMP Tue Jun 30 19:49:51 UTC 2009 i686 GNU/Linux

Zach

---

### Post by metacell on 2009-07-19
KVM requires a processor with either the AMD-V or the Intel VT-x extensions. Not all Athlon 64 processors have the AMD-V extensions. You can check the list at <http://en.wikipedia.org/wiki/List_of_AMD_Athlon_64_microprocessors>.

---

### Post by checoimg on 2009-08-26
determine if you can use KVM

$ sudo su

$ egrep '(vmx|svm)' --color=always /proc/cpuinfo

should display something, e.g. like this:


 root@server1:~# egrep '(vmx|svm)' --color=always /proc/cpuinfo
flags           : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush mmx fxsr sse sse2 ht syscall nx mmxext
 fxsr_opt rdtscp lm 3dnowext 3dnow rep_good nopl pni cx16 lahf_lm cmp_legacy svm extapic cr8_legacy 3dnowprefetch
flags           : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush mmx fxsr sse sse2 ht syscall nx mmxext
 fxsr_opt rdtscp lm 3dnowext 3dnow rep_good nopl pni cx16 lahf_lm cmp_legacy svm extapic cr8_legacy 3dnowprefetch
root@server1:~#
 

If nothing is displayed, then your processor doesn't support hardware virtualization, and you must stop here.




But if you do the go to this lnk:  [http://www.howtoforge.com/virtualization-with-kvm-on-ubuntu-9.04](http://www.howtoforge.com/virtualization-with-kvm-on-ubuntu-9.04)

---

