---
title: "sg device mapping keeps changing"
date: 2009-07-06
forum: General Help
---

### Post by zoemdoef on 2009-07-06
Hello all
 
 
Problem:
 
VMWare Server 2 running on Ubuntu 8.04 with a SCSI card (picked up in Ubuntu) connected to a HP DAT tape drive (also picked up in Ubuntu). 
 
The tape drive is mapped to a windows guest using the generic SCSI device the tape drive is connected to e.g. /sg0. 
 
The /sg number for the tape device mapping changes randomly.
 
Thus the tape drive ends up with a random /sg number which causes the link to the guest OS to fail as the guest OS was spesifically set up to use the /sg device.
 
I hope this makes sense. Any assistance will be appreciated.
 
Info obtained sofar:
I have found the sg utilities from Ubuntu and there is a util called sg_persistent which does not seem to work (I might not be using it correctly)

---

### Post by zoemdoef on 2009-08-20
Anyone?
 
Please?
 
I promise I did google this before I posted.... and have not been able to find a solution.

---

