---
title: "while booting PC With ubuntu"
date: 2010-02-20
forum: General Help
---

### Post by sushilkumar on 2010-02-20
I have Ubuntu as well as Windows on my PC.
During booting I see following:

Ubuntu, Linux 2.6.31-20-generic Ubuntu, Linux 2.6.31-20-generic (recovery mode)
 Ubuntu, Linux 2.6.31-19-generic
 Ubuntu, Linux 2.6.31-19-generic (recovery mode)
 Ubuntu, Linux 2.6.31-18-generic
 Ubuntu, Linux 2.6.31-18-generic (recovery mode)
 Ubuntu, Linux 2.6.31-16-generic
 Ubuntu, Linux 2.6.31-16-generic (recovery mode)
 Ubuntu, Linux 2.6.31-14-generic
 Ubuntu, Linux 2.6.31-14-generic  
  Memory test (memtest86+, serial console 11520
 Microsoft Windows XP Professional (on /dev/sda1)

With keyboard arrows I choose windows if i want to boot in windows.

please tell what all these Ubuntu related messages mean and how to remove these.

Regards

---

### Post by plucky on 2010-02-21
> **sushilkumar said:**
> I have Ubuntu as well as Windows on my PC.
During booting I see following:

Ubuntu, Linux 2.6.31-20-generic Ubuntu, Linux 2.6.31-20-generic (recovery mode)
 Ubuntu, Linux 2.6.31-19-generic
 Ubuntu, Linux 2.6.31-19-generic (recovery mode)
 Ubuntu, Linux 2.6.31-18-generic
 Ubuntu, Linux 2.6.31-18-generic (recovery mode)
 Ubuntu, Linux 2.6.31-16-generic
 Ubuntu, Linux 2.6.31-16-generic (recovery mode)
 Ubuntu, Linux 2.6.31-14-generic
 Ubuntu, Linux 2.6.31-14-generic  
  Memory test (memtest86+, serial console 11520
 Microsoft Windows XP Professional (on /dev/sda1)

With keyboard arrows I choose windows if i want to boot in windows.

please tell what all these Ubuntu related messages mean and how to remove these.

Regards

Open **Synaptic Package Manager** and serch for **linux-image** and remove the earlier kernels.

After a kernel upgrade,a new kernel is added to your grub boot list so that if there are problems with the new kernel,you can revert to the older kernel.
It is recommended you keep at least one older kernel just in case you break the latest kernel and need to boot into an older kernel to fix your system.
Also some people recommend a program called "Ubuntu Tweak" which would help you to keep your system net and tidy.

Good Luck

---

