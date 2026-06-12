---
title: "booted linux host inside itself with VMware"
date: 2010-05-03
forum: General Help
---

### Post by ThomasGHenry on 2010-05-03
Hello, 

I'm dual booting XP and Kubuntu. I wanted to use VMware Workstation to boot to my existing raw XP partition inside Kubuntu, not a virtual XP instance. I accidentally booted Kubuntu inside itself. I know this is a big mistake, so I interrupted VMware, which saved the state and closed. I rebooted and now I can't load the Kubuntu partition at boot time. I get a maintenance shell and the Kubuntu partition is read-only. I am able to boot XP as usual. I removed the HDD and tried to mount it on another computer as an external drive and neither partition will be recognized, it just appears to be one device that still mounts and appears empty. From the maintenance shell I can see all the files are still on the Kubuntu partition. 

How can I undo what I did when I accidentally booted Kubuntu inside itself? Is it a matter of unlocking some files somewhere? how can I do that on a RO filesystem?
Thanks!

---

### Post by ThomasGHenry on 2010-05-03
GRUB -> recovery mode -> fsck -> WIN!

---

