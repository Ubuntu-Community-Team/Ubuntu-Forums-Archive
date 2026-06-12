---
title: "VMWare missing, but working after update"
date: 2011-04-21
forum: General Help
---

### Post by SaarkVanSoor on 2011-04-21
I have just updated my 7.10 release to the final release patches/kernel for it (as a step in the process of upgrading the installation to 10.10) when I have come across a very disheartening problem.
 
Prior to this update, I was running VMWare Server 2.0 with its normaal admin console at localhost:8333 and an applet install under Applications -> System Tools -> VMWare Administration Console. Now that I have updated, both these are missing or inoperable.
 
However, the VMs hosted by the machine are still perfectly functional. I can login to the via Remote Desktop or VNC as the case may be. 
 
I can also no longer see the /var/lib/vmware/Virtual Machines folder or any VMWare folder at all, even when using the full root login and permissions. Find and Search also show a disturbing lack of the 64Gb of VMDK files that are the running VMs. 
 
Any clues as to how I can track down this invisible, but functional install? I do not want to proceed with another update until I get a solid backup of the VMDKs.

---

### Post by brpylko on 2011-04-21
can you navigate to the VM folder in the terminal?

---

### Post by SaarkVanSoor on 2011-04-21
Nope. Attempting to cd to /var/lib/vmware results in the "no such file or directory" error.

---

