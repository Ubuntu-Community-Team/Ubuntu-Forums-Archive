---
title: "Ubuntu Server 9.04 Performance"
date: 2009-07-10
forum: General Help
---

### Post by stevezemlicka on 2009-07-10
I just setup Ubuntu Server 9.04 and vmware.  The performance seems poor.  I first noticed it when I installed windows xp as a VM. When I moved the mouse, the pointer would hesitate up to 10 seconds before finally moving.  I also noticed when I am ssh'ed into it, sometimes it hesitates the same before showing what was typed.

Relevant Specs:
Ubuntu 9.04 (Ran the update)
VMware Server 2.0 Build 122956
Athlon 64 X2 5600+
2GB RAM
60GB SATA (50GB OS 10GB Swap)
2x 80GB ATA RAID0 (storage for VM disks/images)

This is a clean ubuntu install with LAMP and VMware.

On a side note, I installed cacti to try to see what the bottleneck is but all I get for the graphs are the red X's.  I made sure mysql was properly registered with PHP as well as made sure "extension=mysql.so" was added to the php.ini.  Not sure about this one but I'm not concerned if we can get ubuntu to run smoother.

---

### Post by stevezemlicka on 2009-07-10
One more thing.  I have setup a vmware server on ubuntu once before (back with ubuntu 7 or maybe even 6).  It has been in production with several VMs running 24x7 for the last couple years without so much as a hiccup (knock on wood).  However, I really don't know much bout linux.  Thanks for all your help, it is greatly appreciated.

---

