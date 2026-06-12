---
title: "Ubuntu performance tip"
date: 2011-12-08
forum: General Help
---

### Post by spookware on 2011-12-08
I thought I would share a quick performance tip in case anyone else ran in to the same problem. I was working on a custom in house application and noticed some performance problems. I discovered that all of my interrupt handlers were pinned to CPU0 in my system.

you can see if this is your case as well with:
```
cat /proc/interrupts
```

If CPU0 has large counts and your other cpus have none or only very few then this issue affects you as well. The problem is that ubuntu is building their kernels with support for CPU hotplug and hot-removal. This is used for virtualization to hot add/remove a cpu from a running virtual machine. 
But on a physical computer it keeps the kernel from properly distributing interrupts to all of the available cpu cores in your computer. The kernel does this because it never knows if any CPU but cpu0 might suddenly be set for hot-removal. 
Frankly this seems silly to me as ubuntu ships the irqbalance daemon by default which is supposed to intelligently distribute your interrupt handlers based on available cores and power use profiles. But with ubuntus stock kernel irqbalance is not able to do its job because the kernel will refuse to move interrupt handlers off of CPU0 (again because it fears the  other CPUs might disappear in the future). So right now ubuntu is shipping a root level daemon by default that is sitting around and doing nothing.

The solution is to add a couple of boot parameters to the kernel command line. What you need to do is pass "maxcpus" and "possible_cpus" options to the kernel.

To do this edit "/etc/default/grub" file. replace the line that reads
```
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash "
```
with one that reads
```
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash maxcpus=4 possible_cpus=4 "
```

Don't neglect the trailing space character after your last parameter. The example is for a quad core cpu. If you have a dual core then change the '4' to '2', or however many CPUs you actually have.
then run:
```
sudo update-grub
```
and reboot.

check your /proc/interrupts file again and you should find that your IRQ's are now properly distributed across all of your cores. 

As stated I did this to fix a performance problem with a custom application but strangely enough I found that is greatly improved boot time on this computer as well. Hope this helps you as well.

Cheers,
spookware

---

### Post by thaelim on 2011-12-08
Awesome tip - probably belongs in the Tutorials and Tips section though. And I hope you filed a bug against this! :)

---

