---
title: "Linux SATA controller driver - how to update?"
date: 2011-10-15
forum: General Help
---

### Post by listerdl on 2011-10-15
How do I check to see my Linux SATA controller driver is outdated?

**Reason:**

I get this error twice every second in my log viewer:

Oct 15 19:23:38 bt kernel: [ 2351.736105] ata2: SATA link down (SStatus 0 SControl 310)
Oct 15 19:23:38 bt kernel: [ 2351.736128] ata2: EH complete

I am positive that this is related to the SATA Driver being outdated.

PS I tried using different hard drives and always the same issue.

THANKS!!

---

### Post by listerdl on 2011-10-15
OK I have found my driver which is: Intel Corporation ICH9M/M-E SATA AHCI Controller

- After googling it does seem that this SATA driver has been a problem for some people - 

Intel have updated this driver as per this [link]("http://www.radarsync.com/drivers/d176831-intel%28r%29_ich9m%2Fm-e_family_4_port_sata_ahci_controller_-_2929") BUT it only appears to be made available for windows. 

If there is no linux version for this driver then am I always going to have this issue?

There does not seem to be a solution....

---

