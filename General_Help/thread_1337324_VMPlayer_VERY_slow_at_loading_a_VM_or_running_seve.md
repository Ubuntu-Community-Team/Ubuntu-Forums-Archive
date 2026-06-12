---
title: "VMPlayer VERY slow at loading a VM or running several VMs"
date: 2009-11-25
forum: General Help
---

### Post by nick2000 on 2009-11-25
Hello,

I have a strange problem with VMPlayer. This is with VMPlayer 3.0 but VMPlayer 2.5.3 had the same issue.
I am running a Core2Duo 2.4GHz with 4GB of RAM and Ubuntu 9.10 64bit.

The symptoms involve more than 1 VM loaded. It used to be that I could run 4 VMs with no problem (with Ubuntu 7.10 and VMPlayer 1.0) but not anymore. As soon as I get more than 1 VM, VMPLayer slows down EVERYTHING to the point that Ubuntu itself is barely useable. The mouse is jerky as if VMPlayer was basically holding the CPU with interrupts disabled or something. I thought that maybe my disks were the cause (slow IOs?) but moving disks around did not do anything.

A single VM works just fine so it looks like it does not handle multiple VMs correctly. Hibernating a VM while another one is running can take 20minutes during which my mouse pointer (in Ubuntu) can barely register mouse movements!!!

I have looked everywhere but do not seem to find anybody with the same issue. I tried many tricks for boosting VMs performance (temp area in RAM drive, etc...). Throughput to the drives is about 25MB/s but I noticed that the drive icons in VMPlayer stay "lit/active" when the system is slow. How can I troubleshoot this?

I have contemplated switching to KVM or VirtualBox but I have a LOT of existing VMs (this is a development and testing environment). I also have no experience with KVM itself.

Nick

---

