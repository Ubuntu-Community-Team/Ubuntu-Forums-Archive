---
title: "A &quot;bare metal&quot; virtualization for desktop?"
date: 2011-07-22
forum: General Help
---

### Post by arcull on 2011-07-22
Hi all,
I would like to try putting some kind of free "bare metal" virtualization for desktop useage on my laptop. I've been googling about the possibilities, but still I'm not sure which would actually  work in my case. I've seen VMWare ESXi which looks ok, but unfortunatelly it is meant for servers and I can't have ESXI and Sphere client on same laptop :( Another candidate I found is KVM, but as much I've seen it requires VTx VTd support from hardware, which my laptop can't provide. The same requirements must be met for Citrix Xen Client, which is meant for desktop virtualizations, but because of lack of VTx and VTd, can't be used in my case. Is there any other possibility? Currently I'm using VirtualBox and VMWare player for virtualization purposes, but I would like to pull out more performance out of it, and a heavy OS on top of another heavy OS just isn't the best way. Do you have any other suggestion. Thanks for your help.

---

### Post by arcull on 2011-07-25
What do you think about this solution. I could put a little linux distro with VirtualBox on hardware and use this as hypervisor. Would this work well enough? Which distro would be most appropirate. Thanks again.

---

### Post by arcull on 2011-07-26
Since mini linux distros are and probably not as functional as more mature distros, I'm thinking of putting ubuntu server on hardware and install xserver and virtualbox in it. Would that increase performance copared to desktop version of Ubuntu. I mean if virtualbox could use more free resources and therefore possible supply better virtualization? What about graphic card drivers, can they be installed even if I have no dekstop? Thanks for suggestions.

---

