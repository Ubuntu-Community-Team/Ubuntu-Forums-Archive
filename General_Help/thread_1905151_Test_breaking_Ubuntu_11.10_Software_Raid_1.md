---
title: "Test breaking Ubuntu 11.10 Software Raid 1"
date: 2012-01-06
forum: General Help
---

### Post by FiniteRed on 2012-01-06
Hi

I have recently set-up a software raid 1 server system:

[I]md1 : active raid1 sda5[0] sdb5[1]
      522228 blocks super 1.2 [2/2] [UU]
      
md0 : active raid1 sda1[0] sdb1[1]
      33028024 blocks super 1.2 [2/2] [UU]
      
unused devices: <none>[/I]

All seems to work fine, however when I test the system recovery by pulling the power cable of one of the two mirrored disks (while system is off) Ubuntu subsequently fails to boot and the system endlessly restarts after the grub loading timer has expired :S

Iv spend a while Google'ing this but have come up with nothing useful :S Has anyone got any ideas?

Thanks in advance

FR

---

