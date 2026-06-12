---
title: "RAID5 running, need advice on safety"
date: 2009-11-06
forum: General Help
---

### Post by MrRalph on 2009-11-06
Hi all,

I'm very new to Ubuntu server, and just created my first DIY NAS. OS runs on a 160Gb 2.5" HDD (sda) and with mdadm I configured a RAID5 config with 3x WD Green 1Tb's (sd/b/c/d). /dev/md0 is up and running, 2Tb free. So far so good.

Two checks. 

1. If my start up disk fails (the 160Gb 2.5") I'd like to boot from USB and still be able to access the md0. So how do I copy the info about the RAID configuration to a USB-bootable drive for emergencies? Like a emergency-boot disk including my systems configuration.

2. mdadm had a monitor function I like to use to check on the RAID drives. If I start it from the command prompt, it keeps running. How do I start it in the background at boot time so it doesn't occupy my command prompt?

Thanks for any suggestions,

Ralph

---

