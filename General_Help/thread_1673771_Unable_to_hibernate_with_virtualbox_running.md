---
title: "Unable to hibernate with virtualbox running"
date: 2011-01-22
forum: General Help
---

### Post by harbhag on 2011-01-22
Hi all, I am having problem hibernating and suspending my Dell Laptop while virtualbox is running( XP Guest). I have tried default kernel method, uswsusp and tuxonice and none of them works. But if I close virtualbox, then hibernation and suspend works fine. Following are system specs. OS : Ubuntu 10.10 64bit (completey updated) Ram : 4GB Swap : 8 GB Root : 500 GB (of which, about 79% is free)

My laptop model is Dell Inspiron N5010. It has ATI HD 5000 series graphic chipset and I am used proprietary Drivers for it, installed via jockey.

Thanks.

---

### Post by dcstar on 2011-01-23
> **harbhag said:**
> Hi all, I am having problem hibernating and suspending my Dell Laptop while virtualbox is running( XP Guest). I have tried default kernel method, uswsusp and tuxonice and none of them works. But if I close virtualbox, then hibernation and suspend works fine. Following are system specs. OS : Ubuntu 10.10 64bit (completey updated) Ram : 4GB Swap : 8 GB Root : 500 GB (of which, about 79% is free)

My laptop model is Dell Inspiron N5010. It has ATI HD 5000 series graphic chipset and I am used proprietary Drivers for it, installed via jockey.

Thanks.

Your host O/S has no control over the VM and the resources the VM uses when it is running. Until the VM gives back those resources then the host cannot save the running environment with confidence.

If you manually put a script in the Suspend/Hibernate code to manually shut down any VMs in an orderly manner then it may work without corrupting your VMs.

Please put **all** VM issues in the Virtualization forum.

---

### Post by facundobatista on 2011-07-27
I have the same problem than the OP.

Note that the physical machine is unable to sleep/hibernate when Virtualbox *is installed*, even if it's not running.

If I uninstall Virtualbox, sleep/hibernate works ok.

---

