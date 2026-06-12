---
title: "Strange intermittent suspend problem"
date: 2010-11-01
forum: General Help
---

### Post by SickBeast on 2010-11-01
Under Linux, my computer freezes while trying to "sleep". The strange thing is, it works fine the first time my computer sleeps after I boot it up. The second time around, however, my monitor fails to power down, several of the fans in my case continue spinning, and then my computer becomes completely unresponsive.

This issue happens under the following distros:

Ubuntu 10.10 x64
Ubuntu 10.10 32-bit
Peppermint Ice
Ubuntu 10.04.1 x64
Mint Debian
OpenSuse 11.3 x64

This issue does *not* happen under Windows!

I've tried changing just about every setting possible in my BIOS. I loosened the memory timings, tried enabling and disabling 64-bit hardware memory remapping, and I tried disabling Cool N Quiet.

My rig:

Opteron 165
Asus A8N-E (Nforce 4 motherboard)
4gb DDR ram
8800GTS 320mb

I also tried pulling out my memory sticks and running with just one stick of ram. This did nothing to solve the problem.

If any of you have any insight into this problem I would really appreciate it!

TIA

---

### Post by fallingleaf on 2010-11-20
I'm having the same issue on my Dell Studio 1537 laptop with 10.10 x64.  I followed the instructions [here]("http://www.ubuntugeek.com/fix-for-suspend-and-hibernation-problem-for-laptops.html") to use s2ram as the default suspend method.  I'll just have to wait and see if the problem is fixed as my problem can't be reliably reproduced.

---

### Post by Garandir on 2010-11-20
Try adding acpi=off to the end of /boot/grub/menu.list
There will be a line similar to this:

kernel          /boot/vmlinuz-2.6.12-10-686 root=/dev/hda2 ro quiet splash

Thus giving you:
kernel          /boot/vmlinuz-2.6.12-10-686 root=/dev/hda2 ro quiet splash acpi=off

---

### Post by crf on 2010-11-23
I Have this problem.

The Computer use to suspend fine. For the last week, it has had frequent but intermittent inability to suspend. I recently upgraded to ubuntu 10.10 from 10.08, but I think these problems started sometime after that.

What happens is that it goes through some of the motions of suspending.
The screen goes dark, and some boot log text is shown.
Then the CPU starts racing, and the fan comes whirring on. I have to hard reset the laptop by holding down the power button.

So I think it is caught in an infinite loop somewhere.

Also, while it is caught in this loop, power management is working: the screen dims slightly when I pull the power cable out.

dmesg and pm-suspend.log don't seem to show anything different between good suspends or bad ones.

---

### Post by fallingleaf on 2010-11-24
> **crf said:**
> I Have this problem.

The Computer use to suspend fine. For the last week, it has had frequent but intermittent inability to suspend. I recently upgraded to ubuntu 10.10 from 10.08, but I think these problems started sometime after that.

What happens is that it goes through some of the motions of suspending.
The screen goes dark, and some boot log text is shown.
Then the CPU starts racing, and the fan comes whirring on. I have to hard reset the laptop by holding down the power button.

So I think it is caught in an infinite loop somewhere.

Also, while it is caught in this loop, power management is working: the screen dims slightly when I pull the power cable out.

dmesg and pm-suspend.log don't seem to show anything different between good suspends or bad ones.

This definitely is a new problem with 10.10 in my case also.  I did a clean install from using 10.04 before.

crf, are you sure power management is dimming the screen?  On some laptops there is a bios setting that dims the screen.

Another question for anyone with this issue: how does hibernate work for you?  In my case it takes about 5 minutes to hibernate and another 5 to wake up.

---

### Post by crf on 2010-11-27
I'm not certain if it was pm dimming the screen or some bios function. 

Hibernate works with the normal ubuntu kernel.

---

I tried intalling kernel mainline.
[http://kernel.ubuntu.com/~kernel-ppa/mainline/](http://kernel.ubuntu.com/~kernel-ppa/mainline/)
[https://wiki.ubuntu.com/Kernel/MainlineBuilds?action=show&redirect=KernelMainlineBuilds](https://wiki.ubuntu.com/Kernel/MainlineBuilds?action=show&redirect=KernelMainlineBuilds)

This seemed to fix the suspend to ram problem for me. 

However, it breaks hibernation (every time it does something to the swap partition making it unreadable, so that I have to remake it). I'd be nervous about using this kernel if I was using a hibernate file, rather than a swap partition. (Also, while using this kernel, I had an OOM while browsing with flash enabled -- I'd never had that happen before.)

So for the moment I have to pick my poison ;-).

---

### Post by SickBeast on 2010-11-29
I fixed it!

All you have to do is add:

acpi_sleep=old_ordering

after the kernel that you use in /boot/grub/grub.cfg

---

