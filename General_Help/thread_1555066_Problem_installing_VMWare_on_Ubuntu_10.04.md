---
title: "Problem installing VMWare on Ubuntu 10.04"
date: 2010-08-17
forum: General Help
---

### Post by hanxue on 2010-08-17
Hi,


I am trying to install VMware server 2.0.2 on Ubuntu 10.04 LTS. Output of uname -a

```
Linux ip-xx-xx-xx-xx 2.6.32-305-ec2 #9-Ubuntu SMP Thu Apr 15 04:14:01 UTC 2010 i686 GNU/Linux
```Installation works fine, until the point I run vmware-config.pl .  It will attempt to compile vmmon and result in this error:


```
/tmp/vmware-config13/vmmon-only/linux/hostif.c: In function âHostIF_APICInitâ:
/tmp/vmware-config13/vmmon-only/linux/hostif.c:2594: error: âFIX_APIC_BASEâ undeclared (first use in this function)
/tmp/vmware-config13/vmmon-only/linux/hostif.c:2594: error: (Each undeclared identifier is reported only once
/tmp/vmware-config13/vmmon-only/linux/hostif.c:2594: error: for each function it appears in.)
/tmp/vmware-config13/vmmon-only/linux/hostif.c: In function âHostIF_APIC_IDâ:
/tmp/vmware-config13/vmmon-only/linux/hostif.c:2639: error: âFIX_APIC_BASEâ undeclared (first use in this function)
/tmp/vmware-config13/vmmon-only/linux/hostif.c:3601:2: warning: #warning current->cred->fsuid = 0;
/tmp/vmware-config13/vmmon-only/linux/hostif.c:3608:2: warning: #warning current->cred->fsuid = fsuid;
/tmp/vmware-config13/vmmon-only/linux/hostif.c:3626:2: warning: #warning cap_lower(current->cred->cap_effective, CAP_SYS_RESOURCE);
make[2]: *** [/tmp/vmware-config13/vmmon-only/linux/hostif.o] Error 1
make[1]: *** [_module_/tmp/vmware-config13/vmmon-only] Error 2
make: *** [vmmon.ko] Error 2
For more information on how to troubleshoot module-related problems, please
visit our Web site at "http://www.vmware.com/go/unsup-linux-products" and
"http://www.vmware.com/go/unsup-linux-tools".
```Note that this is after applying the patches from     [http://communities.vmware.com/thread/267682](http://communities.vmware.com/thread/267682)
  
Any hints what I may be missing?


Thanks in advance,
Hanxue

---

### Post by dcstar on 2010-08-18
> **hanxue said:**
> Hi,


I am trying to install VMware server 2.0.2 on Ubuntu 10.04 LTS. Output of uname -a
.......

Look in the Virtualization forum for all VM issues.

---

### Post by hanxue on 2010-08-18
David,


Thanks for the advice. I have posted it on the Virtualization forum. I searched on Ubuntu forums, VMWare forums and googled as well, cannot find a similar situation. 


Cheers,
Hanxue

---

### Post by Sef on 2010-08-18
OP has posted the message elsewhere, so locked.

---

