---
title: "Security risks of running XP through VMware?"
date: 2006-02-13
forum: General Help
---

### Post by Protex on 2006-02-13
Hi guys.

Do I need to install a firewall and anti-virus in an XP installation I am running through VMware?

---

### Post by Jedeye on 2006-02-13
lol... I find that funny. Not sure though... but it probably wouldnt be a bad idea.. as long as it dosent slow the VMware down to much.

---

### Post by RAOF on 2006-02-13
As I understand it, the XP you've got running under VMware is the real-deal.  It's an actual Windows install, just on "fake" hardware.  As such, it's probably just as vulnerable as any other XP system.  Although it shouldn't be able to take down the whole computer, just the virtual machine.

There are some exceptions - last time I checked (which was a while ago), the networking was chained through the kernel ipchains NAT, so there's already a certain amount of network filtering going on.  But I'd treat a XP install under VMware as a normal XP install, so firewall & anti-virus away!

---

### Post by Protex on 2006-02-14
Hrm, okay.

Any other suggestions?

---

### Post by Harry_Sack on 2006-02-15
Yeah, I'm just going to never connect it.

---

### Post by udha on 2006-02-15
I've only ever tried XP under linux using qemu, and I used the snapshot feature, so I installed what I wanted then created a snapshot, then next time it ran it would not touch the image, and any changes made would be lost when the virtual session was closed, this is secure.

If you keep all settings inside the VM then your XP will be vulnerable, but if you are not running the VM as root or a privileged user, your linux system will be perfectly safe.

---

