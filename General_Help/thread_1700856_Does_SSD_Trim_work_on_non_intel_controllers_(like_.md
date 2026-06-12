---
title: "Does SSD Trim work on non intel controllers? (like jmicron, or nvidia)"
date: 2011-03-05
forum: General Help
---

### Post by Krause on 2011-03-05
In windows the only controllers that really work with TRIM is the onboard Intel ones, Jmicron, Marvell, Nvidia and AMD's don't pass the command to the drives if you use their own drivers.(and from what Ive read, the Micron sata6 controllers dont work with TRIM even using the default Microsoft drivers)

In Linux do more then just Intel drives work with TRIM? I have a Nvidia 790i Ultra motherboard, the SATA controller is an Nvidia one which has 2 settings, ATA and Raid (if the drives aren't added to an array it runs them in AHCI) and has an additional Jmicron sata port.

If I enabled TRIM in the OS, would it work on either of those controllers?

Also if anyone knows this, in Windows if you set an Intel controller to raid, you wont get TRIM on SSD's that are on the controller (but not in an array) with the default Microsoft driver like you would if it was set to AHCI, you only get it with the Intel RST drivers. Would a SSD on an Intel controller set to raid but not in an array get the TRIM command passed to it in Ubuntu?

---

### Post by dargaud on 2011-03-05
TRIM is in the process of being standardized, so it's (going to be) used by other SSDs as well. You should be able to test it with the latest versions of hdparm, although I must say I know nothing about it as I still bitbang my SSDs at the GPIO level...

---

