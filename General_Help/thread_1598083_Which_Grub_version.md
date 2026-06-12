---
title: "Which Grub version?"
date: 2010-10-16
forum: General Help
---

### Post by simontepper on 2010-10-16
I recently installed 10.04 (upgraded to 10.10) on a Windows 7 machine and can now choose which OS to boot from.

The boot screen gives me a number of options including 2.6.32-22 and 2.6.32-25.

Does it matter which of those I select? Am I correct in assuming that ...32-25 is the more recent? Does it make a difference? The end result seems to be the same (i.e. a speedy boot into Ubuntu).

---

### Post by efflandt on 2010-10-16
The kernel with the highest number at the top of the grub menu will be the newest kernel.

Later on if you end up with too many kernels listed you can uninstall earlier version Linux images and headers using Synaptic.  Although, it is best to leave one previous kernel besides the current kernel in case something with a new one is incompatible with your system.  Sometimes the most recent kernel will be updated multiple times (not sure if different compile options or added modules), but if that is the only kernel you have and an update to that kernel does not work, you are stuck.

---

### Post by Quackers on 2010-10-16
The latest one is normally the top one in the grub menu.

---

### Post by dcstar on 2010-10-16
> **simontepper said:**
> 
..........
The boot screen gives me a number of options including 2.6.32-22 and 2.6.32-25.

Does it matter which of those I select? Am I correct in assuming that ...32-25 is the more recent? Does it make a difference? The end result seems to be the same (i.e. a speedy boot into Ubuntu).

Later kernels have security patches and should be used - but **always** keep (at least) two kernels in your system in case one gets broken so you can use the other to try and repair your system

---

### Post by simontepper on 2010-10-17
thanks, guys. One small query answered! :smile:

---

