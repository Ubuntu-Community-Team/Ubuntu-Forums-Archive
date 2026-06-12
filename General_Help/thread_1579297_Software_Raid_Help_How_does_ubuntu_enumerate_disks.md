---
title: "Software Raid Help: How does ubuntu enumerate disks"
date: 2010-09-21
forum: General Help
---

### Post by pormogo on 2010-09-21
So I am going to be adding a mdadm RAID5 array to my shell box/file server later on today. I've done software RAID under linux before so I'm not terribly nervous about the mdadm setup. However there is something slightly odd about this box that I am worried about, and that is how the drives on the system are encounted for in /dev after the system boots. There are 4 drives attached to the 4 SATA controller ports on the mobo (2 of which are managed by the southbridge and 2 of which are managed by an additional SATA controller installed on the mobo "MSI K8T Neo"). These drives seem to "shuffle" around as the system reboots. For example sometimes  Ubuntu decides to enumerate my boot drive as /dev/sdc* sometimes it likes to make it /dev/sdd* rarely it decides that drive should now be /dev/sda*. My worry here is that at some point I'll reboot this machine and it'll device to shuffle around which drives are which called which device and suddenly my array will be broken. Any help is greatly appreciated.

---

### Post by pormogo on 2010-09-22
Bumping this, I was planning on building the array later tonight and wanted to see if there was any advice.

---

