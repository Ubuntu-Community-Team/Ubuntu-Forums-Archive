---
title: "Can't boot with IOMMU enabled"
date: 2009-10-22
forum: General Help
---

### Post by Particle on 2009-10-22
Hello folks.

I'm trying to install Ubuntu 9.10 to a new computer with AMD-Vi technology (directed I/O, IOMMU) so that I can install Xen and use it as an advanced VM server to serve as a multi-user 3D terminal with dedicated GPU hardware for each console.

However, Ubuntu hangs on boot when the IOMMU unit is engaged.  If I disable it, everything works fine.  However, the whole reason I need Ubuntu on here in the first place depends on the IOMMU unit working.

Any ideas?

---

### Post by P4man on 2009-10-22
Are you using first gen Barcelona cpu's? Didnt they have this IOMMU (hardware)  bug? I could be dead wrong though.
edit: guess not, it was TLB bug

---

### Post by Particle on 2009-10-22
I am using the latest generation--Istanbul CPUs with the newly launched AMD SR5690 chipset.  Both support the new IOMMU technology.  Perhaps it's too new to be supported yet?  The first boards only came out a month ago.  AMD demoed this working on Xen, but I don't think it was with Ubuntu as the OS.

---

