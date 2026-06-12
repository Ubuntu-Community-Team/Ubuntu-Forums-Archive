---
title: "LVM Advice"
date: 2011-11-05
forum: General Help
---

### Post by tsumaru on 2011-11-05
Hi, 

I have just upgraded my server to some new hardware and its all going great. My old server had a 4TB LVM array and a 500G Raid 1 array. All the disks are in and working fine, my Raid array is doing its sync and my LVM array is up and running!

I currently have 9 disks. 

1x160GB System Disk
2x500GB Raid 1
3x1TB, 2x750GB and 1x500G in the LVM Array. 

My question to you is, what would be the better configuration with regard to having the devices connected to the machine?

The Motherboard has 6 Sata slots and I have a PCI Expansion card that provides another 4 slots.

I currently have the 160G drive connected to the Mobo and the arrays as follows:

1x750G, 1x1TB, 1x500G From the LVM Array connected to the PCI card
1x750G, 2x1TB from the LVM array connected to the Mobo.

of the 2x500Gs in the Raid array, one is connected to the Mobo and one to the PCI card

Would I get better performance if all my LVM devices were connected to the Mobo or is it better to split them accross the two controllers?

Thanks

---

