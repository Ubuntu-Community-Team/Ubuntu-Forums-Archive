---
title: "Presario CQ56"
date: 2010-11-30
forum: General Help
---

### Post by stoney39 on 2010-11-30
Hi 
I have a Presario CQ56-134CA netbook. Intel Pentium Processor T4500,320GB Hd, 3 Gig of memeory. Intel Graphics Media Accelerator 4500M with shared memoroy. I been having a hard time partitioning the hard so I can install Ubuntu 10.10 or any linux distro. When I go to try and install it will not let me partition the drive. I was wondering if anyone else owns the same laptop and has had success dual booting this particular machine.

---

### Post by dcstar on 2010-11-30
> **stoney39 said:**
> Hi 
I have a Presario CQ56-134CA netbook. Intel Pentium Processor T4500,320GB Hd, 3 Gig of memeory. Intel Graphics Media Accelerator 4500M with shared memoroy. I been having a hard time partitioning the hard so I can install Ubuntu 10.10 or any linux distro. When I go to try and install it will not let me partition the drive. I was wondering if anyone else owns the same laptop and has had success dual booting this particular machine.

Boot off the USB installer and manually run **gparted** to shrink your existing partition to make room for Ubuntu.

You will need 10GB of space for the new "/" partition and 3GB for Swap.

---

