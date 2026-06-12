---
title: "kdump"
date: 2010-10-20
forum: General Help
---

### Post by ub007 on 2010-10-20
just wished to get some clarification on 'kdump' functionality

As per my understanding, if kdump is enabled/operational -when a crash occurs, capture kernel is booted via 'kexec'. But this mechanism is a kernel-to-kernel bootloader, so it boots into the new kernel over reboot w/o going through BIOS.

question is 
On Scenario:
- System crashes/panics
-boots from the capture kernel
-I copy the dump across or analyse them using utils like crash etc.
-Now to start using the server as normal do I have to do a reboot?
(The fact that kexec skips the entire bootloader stage and directly jumps into the kernel that we want to boot to gets me bit worried.
BIOS stage always initializes (or resets) the devices to a known "sane" state. The fact that kexec bypasses this stage means that the state of the devices is unreliable. ) [COLOR="Red"]So is a reboot neccessary?[/COLOR]

thanks
David

---

